# Semantic kernel examples


## Simple 

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

## DeepSeek example

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

## Token usage

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

## Simple text completions

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


