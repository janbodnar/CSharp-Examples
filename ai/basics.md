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
