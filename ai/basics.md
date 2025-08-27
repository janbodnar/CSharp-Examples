# Semantic kernel examples


## Simple 

This example demonstrates the most basic usage of Microsoft Semantic Kernel. It shows how to create a kernel instance, configure it with an OpenAI-compatible chat completion service (using OpenRouter as a proxy), and make a simple prompt request.

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

The kernel processes the prompt and returns the AI's response directly as a string. This is the simplest way to get started with Semantic Kernel for basic question-answering scenarios.

## DeepSeek example

This example shows how to use DeepSeek's API directly with Semantic Kernel. It demonstrates working with chat completion services and managing conversation history, including system and user messages for more structured interactions.

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

This approach provides more control over the conversation flow and allows you to maintain context across multiple exchanges. The system message helps establish the AI's role and behavior.

## Token usage

This example demonstrates how to monitor and track token consumption when using AI APIs. Understanding token usage is crucial for cost management and optimizing API calls in production applications.

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

The output shows the breakdown of tokens used: input tokens (your prompt), output tokens (AI's response), and total tokens. This information helps you understand and optimize your API costs.

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

This example shows how to configure completion settings to fine-tune the AI's responses. By adjusting parameters like maximum tokens and temperature, you can control the length and creativity of the generated text.

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

The `MaxTokens` setting limits response length (useful for concise answers), while `Temperature` controls randomness - lower values (0.1-0.3) give more focused responses, higher values (0.7-1.0) produce more creative and varied outputs.


