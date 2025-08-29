# Semantic kernel examples


## Simple 

This example demonstrates the most basic usage of Microsoft Semantic Kernel. It shows how to create a  
kernel instance, configure it with an OpenAI-compatible chat completion service (using OpenRouter as a proxy),  
and make a simple prompt request.

```c#
using Microsoft.SemanticKernel;


var builder = Kernel.CreateBuilder();

builder.AddOpenAIChatCompletion(
    modelId: "anthropic/claude-3-haiku",
    apiKey: Environment.GetEnvironmentVariable("OPENROUTER_API_KEY"),
    endpoint: new Uri("https://openrouter.ai/api/v1")
);

var kernel = builder.Build();
var result = await kernel.InvokePromptAsync("Is Pluto a planet?");
Console.WriteLine(result);
```

The kernel processes the prompt and returns the AI's response directly as a string. This is the simplest  
way to get started with Semantic Kernel for basic question-answering scenarios.

## DeepSeek example

This example shows how to use DeepSeek's API directly with Semantic Kernel. It demonstrates working  
with chat completion services and managing conversation history, including system and user messages  
for more structured interactions.

```c#
using Microsoft.SemanticKernel;
using Microsoft.SemanticKernel.ChatCompletion;


var builder = Kernel.CreateBuilder();
builder.AddOpenAIChatCompletion(
    modelId: "deepseek-chat",
    apiKey: Environment.GetEnvironmentVariable("DEEPSEEK_API_KEY"),
    endpoint: new Uri("https://api.deepseek.com")
);

var kernel = builder.Build();
var chatCompletionService = kernel.GetRequiredService<IChatCompletionService>();

var chatHistory = new ChatHistory();
chatHistory.AddSystemMessage("You are a helpful assistant");
chatHistory.AddUserMessage("Is Pluto a planet?");

var result = await chatCompletionService.GetChatMessageContentAsync(chatHistory);
Console.WriteLine(result.Content);
```

This approach provides more control over the conversation flow and allows you to maintain  
context across multiple exchanges. The system message helps establish the AI's role and behavior.

## Token usage

This example demonstrates how to monitor and track token consumption when using AI APIs.  
Understanding token usage is crucial for cost management and optimizing API calls in  
production applications.

```c#
using Microsoft.SemanticKernel;
using Microsoft.SemanticKernel.ChatCompletion;
using OpenAI.Chat;


var builder = Kernel.CreateBuilder();
builder.AddOpenAIChatCompletion(
    modelId: "deepseek-chat",
    apiKey: Environment.GetEnvironmentVariable("DEEPSEEK_API_KEY"),
    endpoint: new Uri("https://api.deepseek.com")
);

var kernel = builder.Build();
var chatCompletionService = kernel.GetRequiredService<IChatCompletionService>();

var chatHistory = new ChatHistory();
chatHistory.AddSystemMessage("You are a helpful assistant");
chatHistory.AddUserMessage("Is Pluto a planet?");

var result = await chatCompletionService.GetChatMessageContentAsync(chatHistory);
Console.WriteLine("Assistant: " + result.Content);

// foreach (var kvp in result.Metadata)
// {
//     Console.WriteLine($"{kvp.Key}: {kvp.Value}");
// }


// Print token usage details
if (result.Metadata != null && result.Metadata.TryGetValue("Usage", out var usageObj) && usageObj is ChatTokenUsage usage)
{
    Console.WriteLine("\nToken Usage:");
    Console.WriteLine("Prompt tokens: " + usage.InputTokenCount);
    Console.WriteLine("Completion tokens: " + usage.OutputTokenCount);
    Console.WriteLine("Total tokens: " + usage.TotalTokenCount);
}
```

The output shows the breakdown of tokens used: input tokens (your prompt), output tokens (AI's response),  
and total tokens. This information helps you understand and optimize your API costs.  

## Streaming 

```c#
using Microsoft.SemanticKernel;
using Microsoft.SemanticKernel.ChatCompletion;

var builder = Kernel.CreateBuilder();
builder.AddOpenAIChatCompletion(
    modelId: "x-ai/grok-code-fast-1",
    apiKey: Environment.GetEnvironmentVariable("OPENROUTER_API_KEY"),
    endpoint: new Uri("https://openrouter.ai/api/v1")
);

var kernel = builder.Build();
var chatCompletionService = kernel.GetRequiredService<IChatCompletionService>();

// Create chat history with user message
var chatHistory = new ChatHistory();
chatHistory.AddUserMessage("Is Pluto a planet?");

// Enable streaming in the completion request
Console.Write("Streaming response:");
await foreach (var chunk in chatCompletionService.GetStreamingChatMessageContentsAsync(chatHistory))
{
    // Check if the chunk contains content
    if (!string.IsNullOrEmpty(chunk.Content))
    {
        // Print the content chunk without a newline
        Console.Write(chunk.Content);
    }
}

// Add a final newline for clean formatting
Console.WriteLine();
```


## Simple text completions

This example shows how to configure completion settings to fine-tune the AI's responses. By adjusting  
parameters like maximum tokens and temperature, you can control the length and creativity 
of the generated text.

```c#
using Microsoft.SemanticKernel;
using Microsoft.SemanticKernel.Connectors.OpenAI;


var builder = Kernel.CreateBuilder();
builder.AddOpenAIChatCompletion(
    modelId: "z-ai/glm-4.5-air:free",
    apiKey: Environment.GetEnvironmentVariable("OPENROUTER_API_KEY"),
    endpoint: new Uri("https://openrouter.ai/api/v1")
);

var kernel = builder.Build();

var settings = new OpenAIPromptExecutionSettings
{
    MaxTokens = 150,
    Temperature = 0.7f
};

var arguments = new KernelArguments(settings);
var result = await kernel.InvokePromptAsync("Is Pluto a planet?", arguments);
Console.WriteLine(result);
```

The `MaxTokens` setting limits response length (useful for concise answers), while `Temperature`  
controls randomness - lower values (0.1-0.3) give more focused responses, higher values (0.7-1.0)  
produce more creative and varied outputs.

## Multi-turn conversation

```c#
using Microsoft.SemanticKernel;
using Microsoft.SemanticKernel.ChatCompletion;

var builder = Kernel.CreateBuilder();
builder.AddOpenAIChatCompletion(
    modelId: "z-ai/glm-4.5-air:free",
    apiKey: Environment.GetEnvironmentVariable("OPENROUTER_API_KEY"),
    endpoint: new Uri("https://openrouter.ai/api/v1")
);

var kernel = builder.Build();
var chatCompletionService = kernel.GetRequiredService<IChatCompletionService>();

// Initialize messages for multi-turn conversation
var chatHistory = new ChatHistory();
chatHistory.AddUserMessage("What is the capital of France? Answer in one sentence.");

// First turn: Ask about France
var completion = await chatCompletionService.GetChatMessageContentAsync(chatHistory);

// Get and store the response
var franceResponse = completion.Content ?? "No response";
chatHistory.AddAssistantMessage(franceResponse);

Console.WriteLine("First question response: " + franceResponse);

// Second turn: Ask about Slovakia
chatHistory.AddUserMessage("And of Slovakia?");

completion = await chatCompletionService.GetChatMessageContentAsync(chatHistory);

// Print the final response
Console.WriteLine("Second question response: " + (completion.Content ?? "No response"));
```

## Function call 

```c#
using Microsoft.SemanticKernel;
using Microsoft.SemanticKernel.ChatCompletion;
using Microsoft.SemanticKernel.Connectors.OpenAI;

public class TranslationPlugin
{
    public static string? SelectedLanguage;
    private static readonly Random Rng = Random.Shared; // 1) reusable randomness

    [KernelFunction(name: "get_random_language")]
    public string GetRandomLanguage()
    {
        string[] languages = ["Spanish", "Czech", "Hungarian", "French",
            "German", "Italian", "Slovak", "Polish", "Russian"];
        // var language = languages[Rng.Next(languages.Length)];
        var random = new Random();
        var language = languages[random.Next(languages.Length)];
        SelectedLanguage = language;
        Console.WriteLine($"[DEBUG] Function called! Selected: {language}");
        return language;
    }
}

public class Program
{
    public static async Task Main()
    {
        // 2) Guard config: API key
        var apiKey = Environment.GetEnvironmentVariable("DEEPSEEK_API_KEY");
        if (string.IsNullOrWhiteSpace(apiKey))
        {
            Console.Error.WriteLine("DEEPSEEK_API_KEY is not set. Please set it in your environment.");
            return;
        }

        // Build the kernel
        var builder = Kernel.CreateBuilder();
        builder.AddOpenAIChatCompletion(
            modelId: "deepseek-chat",
            apiKey: apiKey,
            endpoint: new Uri("https://api.deepseek.com")
        );

        // Add the plugin
        var plugin = new TranslationPlugin();
        builder.Plugins.AddFromObject(plugin);

        var kernel = builder.Build();
        var chat = kernel.GetRequiredService<IChatCompletionService>();

        // Reset the selected language before each run
        TranslationPlugin.SelectedLanguage = null;

        // Strong system instruction to use the tool
        var messages = new ChatHistory();
        messages.AddSystemMessage("You have access to the get_random_language function. Call it first, then translate the sentence into the returned language.");
        messages.AddUserMessage("Pick a random language using the function, then translate 'Hello, how are you?' into it.");

        // 5) Lower temperature to reduce creative deviations and promote tool use
        var exec = new OpenAIPromptExecutionSettings
        {
            ToolCallBehavior = ToolCallBehavior.AutoInvokeKernelFunctions,
            Temperature = 0.2f,
            MaxTokens = 50
        };

        // First call – model may call the tool and SK will auto-invoke
        var turn1 = await chat.GetChatMessageContentAsync(messages, exec, kernel);

        string language = TranslationPlugin.SelectedLanguage ?? string.Empty;
        if (string.IsNullOrWhiteSpace(language))
        {
            // Fallback: model didn’t actually call the tool. Do it ourselves to match Python flow.
            Console.WriteLine("[INFO] Auto tool invocation didn’t happen. Falling back to direct function call.");
            language = plugin.GetRandomLanguage();
        }

        // Second turn: ask for translation into exactly the selected language
        var messages2 = new ChatHistory();
        messages2.AddSystemMessage("Translate exactly into the specified language. Output only the translation sentence.");
        messages2.AddUserMessage($"Language: {language}. Translate 'Hello, how are you?' into this language.");

        var exec2 = new OpenAIPromptExecutionSettings
        {
            // ToolCallBehavior = ToolCallBehavior.,
            Temperature = 0.2f,
            MaxTokens = 50
        };

        var turn2 = await chat.GetChatMessageContentAsync(messages2, exec2, kernel);

        Console.WriteLine("Language selected: " + language);
        Console.WriteLine("Final translation response:");
        Console.WriteLine(turn2.Content);
    }
}
```

