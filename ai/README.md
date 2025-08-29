

## Simple example

```c#
using Microsoft.SemanticKernel;

var apiKey = Environment.GetEnvironmentVariable("OPENROUTER_API_KEY");
if (string.IsNullOrEmpty(apiKey))
{
    Console.WriteLine("Please set the OPENROUTER_API_KEY environment variable.");
    return;
}

var builder = Kernel.CreateBuilder();
builder.AddOpenAIChatCompletion(
    modelId: "x-ai/grok-code-fast-1",
    apiKey: apiKey,
    endpoint: new Uri("https://openrouter.ai/api/v1")
);

var kernel = builder.Build();

var prompt = @"
Generate a complete HTML file for a 'Holy Grail' layout. The layout should include:
- A header at the top
- A footer at the bottom
- A left sidebar
- A main content area in the center
- A right sidebar

Use CSS Grid or Flexbox for the layout. Make it responsive and include some basic styling.
Provide only the HTML code, no explanations.).
";

var result = await kernel.InvokePromptAsync(prompt);

var htmlContent = result.ToString();

// Strip markdown code blocks from start and end
var cleanedHtml = htmlContent.StartsWith("```html") && htmlContent.EndsWith("```")
    ? htmlContent[7..^3].Trim()
    : htmlContent.Trim();

await File.WriteAllTextAsync("holy_grail.html", cleanedHtml);

Console.WriteLine("HTML file generated: holy_grail.html");
```
