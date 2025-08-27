# Semantic kernel examples


## Simple 

```c#
from openai import OpenAI
import os

# Client initialization with OpenRouter API
client = OpenAI(
    base_url="https://openrouter.ai/api/v1",
    api_key=os.environ.get("OPENROUTER_API_KEY"),
)

# First API call
completion = client.chat.completions.create(
    extra_body={},  # OpenRouter specific parameters
    model="anthropic/claude-3-haiku",  # Model from Anthropic via OpenRouter
    messages=[
        {"role": "user", "content": "Is Pluto a planet?"}
    ]
)

print(completion.choices[0].message.content)
```
