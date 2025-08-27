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

```C#
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
