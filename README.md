# CSharp-Examples

C# Examples


```csharp
using System.Diagnostics;

Console.WriteLine(Environment.CurrentDirectory); // print current working directory

// Execute shell command
var result = Process.Start(new ProcessStartInfo("ls", "-la")
{
    RedirectStandardOutput = true,
    UseShellExecute = false
});

if (result != null)
{
    result.WaitForExit();
    Console.WriteLine(result.StandardOutput.ReadToEnd());
}
else
{
    Console.WriteLine("Failed to start process.");
}
```

## even/odd numbers

```csharp
// Lambda functions for odd/even
Func<int, bool> isOdd = i => (i & 1) == 1;
Func<int, bool> isEven = i => !isOdd(i);

Console.WriteLine(isOdd(3));  // True
Console.WriteLine(isEven(3)); // False


// Filter even values using LINQ
var evens = new[] {1, 2, 3, 4, 5}.Where(it => it % 2 == 0).ToArray();
Console.WriteLine($"[{string.Join(", ", evens)}]"); // [2, 4]
```  


## Creating executable applications with dotnet:

```xml
<!-- In .csproj file -->
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net8.0</TargetFramework>
    <PublishSingleFile>true</PublishSingleFile>
    <SelfContained>true</SelfContained>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

```bash
# Command to create self-contained executable
dotnet publish -c Release -r win-x64 --self-contained true /p:PublishSingleFile=true

# Cross-platform executable
dotnet publish -c Release -r linux-x64 --self-contained true /p:PublishSingleFile=true
```

## var keyword

Using `var` for type inference and `object` for dynamic typing:

```csharp
// Using var - type is inferred at compile time and cannot be reassigned to different types
var x = 12;
Console.WriteLine(x.GetType().Name); // Int32

// Using object - allows reassignment to different types
object y = 12;
Console.WriteLine(y.GetType().Name); // Int32

y = "falcon";
Console.WriteLine(y.GetType().Name); // String
```

## System properties


C# equivalent using Environment class:

```csharp
Console.WriteLine(Environment.Version); // .NET version instead of Java vendor
Console.WriteLine(Environment.Is64BitOperatingSystem ? "x64" : "x86"); // OS architecture
Console.WriteLine(Environment.OSVersion.Platform); // OS platform
Console.WriteLine(Environment.Version); // .NET version instead of Java class version
Console.WriteLine(Environment.CurrentDirectory); // Current directory instead of class path

Console.WriteLine(DateTimeOffset.UtcNow.ToUnixTimeMilliseconds()); // Current time in milliseconds
```

## Environment variables 

Using `Environment` class:

```csharp
Console.WriteLine(Environment.GetEnvironmentVariable("DOTNET_ROOT"));
Console.WriteLine(Environment.GetEnvironmentVariable("HOME")); // or "USERPROFILE" on Windows
Console.WriteLine(Environment.GetEnvironmentVariable("PATH"));

Console.WriteLine("------------------------");

var env = Environment.GetEnvironmentVariables()
    .Cast<DictionaryEntry>()
    .Select(e => $"{e.Key}={e.Value}");

foreach (var e in env)
{
    Console.WriteLine(e);
}
```

## Multiple assignments

Using tuple deconstruction:

```csharp
// Basic tuple deconstruction
var (name1, name2, name3) = ("John Doe", "Roger Roe", "Lucia Smith");
Console.WriteLine(name1);
Console.WriteLine(name2);
Console.WriteLine(name3);

// Typed variables
var (x, y, w) = (10, 20, "falcon");
Console.WriteLine(x); // int
Console.WriteLine(y); // int  
Console.WriteLine(w); // string

// Discard operator
var parts = "3rd August 2023".Split();
var (_, month, year) = (parts[0], parts[1], parts[2]);
Console.WriteLine(month);
Console.WriteLine(year);
```


## Boxing and value types:

```csharp
int n = 3;
Console.WriteLine(n.GetType().Name); // Int32
Console.WriteLine(n.GetType().IsValueType); // True (value types in C#)

float m = 4.4f;
Console.WriteLine(m.GetType().Name); // Single
Console.WriteLine(m.GetType().IsValueType); // True

// Boxing example
object boxedInt = n; // Boxing happens here
Console.WriteLine(boxedInt.GetType().Name); // Int32
Console.WriteLine(boxedInt.GetType().IsValueType); // True (type info preserved)
```

## Steps 

```csharp
// Usage
1.0.Step(4.0, 0.5, x => Console.Write($"{x} "));
Console.WriteLine("\n-----------------------");

1.Step(10, 1, x => Console.WriteLine(x));

// Alternative using LINQ and ranges
var stepSequence = Enumerable.Range(0, (int)((4.0 - 1.0) / 0.5) + 1)
    .Select(i => 1.0 + i * 0.5);

foreach (var value in stepSequence)
{
    Console.Write($"{value} ");
}


// Extension method for step functionality
public static class NumberExtensions
{
    public static void Step(this double start, double end, double step, Action<double> action)
    {
        for (double i = start; i <= end; i += step)
        {
            action(i);
        }
    }
    
    public static void Step(this int start, int end, int step, Action<int> action)
    {
        for (int i = start; i <= end; i += step)
        {
            action(i);
        }
    }
}
```

## Pick random element from list

```csharp
var words = new[] {"sky", "cup", "tall", "falcon", "cloud"};

var rnd = new Random();

var ri = rnd.Next(words.Length);
Console.WriteLine(words[ri]);

// Alternative using LINQ (more concise)
var randomWord = words.OrderBy(x => rnd.Next()).First();
Console.WriteLine(randomWord);
```


## Download image


Using HttpClient:

```csharp
using var httpClient = new HttpClient();
var data = await httpClient.GetByteArrayAsync("http://webcode.me/favicon.ico");
await File.WriteAllBytesAsync("favicon.ico", data);

// Synchronous version
var dataSync = httpClient.GetByteArrayAsync("http://webcode.me/favicon.ico").Result;
File.WriteAllBytes("favicon.ico", dataSync);
```

## Iterate runes

C# equivalent using `StringInfo` or direct string enumeration:

```csharp
using System.Globalization;

var text = "🐜🐬🐄🐘🦂🐫🐑🦍🐯🐞";

// Method 1: Using StringInfo
var stringInfo = new StringInfo(text);
for (int i = 0; i < stringInfo.LengthInTextElements; i++)
{
    Console.WriteLine(stringInfo.SubstringByTextElements(i, 1));
}

Console.WriteLine("----------------");

// Method 2: Using TextElementEnumerator  
var enumerator = StringInfo.GetTextElementEnumerator(text);
while (enumerator.MoveNext())
{
    Console.WriteLine(enumerator.Current);
}

Console.WriteLine("----------------");

// Method 3: Using Rune (C# 8+)
foreach (var rune in text.EnumerateRunes())
{
    Console.WriteLine(rune.ToString());
}
```

## Create a deck of cards


Using LINQ for combinations:

```csharp
var signs = Enumerable.Range(2, 9).Select(n => n.ToString())
    .Concat(new[] {"J", "Q", "K", "A"});
var symbols = new[] {"♣", "♦", "♥", "♠"};

// Create all combinations using LINQ
var cards = from symbol in symbols
           from sign in signs
           select symbol + sign;

var cardList = cards.ToList();
Console.WriteLine($"[{string.Join(", ", cardList)}]");

// Shuffle the deck
var random = new Random();
var shuffledCards = cardList.OrderBy(x => random.Next()).ToList();

// Take first 5 cards
var hand = shuffledCards.Take(5);
Console.WriteLine($"Hand: [{string.Join(", ", hand)}]");

// Alternative shuffle using Fisher-Yates
static void Shuffle<T>(IList<T> list, Random rng)
{
    for (int i = list.Count - 1; i > 0; i--)
    {
        int j = rng.Next(i + 1);
        (list[i], list[j]) = (list[j], list[i]);
    }
}

var deckCopy = cardList.ToList();
Shuffle(deckCopy, random);
Console.WriteLine($"Shuffled: [{string.Join(", ", deckCopy.Take(5))}]");
```

## Shuffle emoji cards

Emoji cards and display function:

```csharp
var cards = new[]
{
    "🂡", "🂱", "🃁", "🃑",
    "🂢", "🂲", "🃂", "🃒",
    "🂣", "🂳", "🃃", "🃓",
    "🂤", "🂴", "🃄", "🃔",
    "🂥", "🂵", "🃅", "🃕",
    "🂦", "🂶", "🃆", "🃖",
    "🂧", "🂷", "🃇", "🃗",
    "🂨", "🂸", "🂸", "🂸",
    "🂩", "🂩", "🃉", "🃙",
    "🂪", "🂺", "🃊", "🃚",
    "🂫", "🂻", "🃋", "🃛",
    "🂭", "🂽", "🃍", "🃝",
    "🂮", "🂾", "🃎", "🃞"
};

static void Show(string[] cards)
{
    for (int i = 0; i < cards.Length; i++)
    {
        if (i != 0 && i % 13 == 0)
        {
            Console.WriteLine();
        }
        Console.Write($"{cards[i]} ");
    }
    Console.WriteLine();
}

// Shuffle cards
var random = new Random();
var shuffledCards = cards.OrderBy(x => random.Next()).ToArray();

Show(shuffledCards);

// Alternative: using Fisher-Yates shuffle
static void ShuffleInPlace<T>(T[] array, Random rng)
{
    for (int i = array.Length - 1; i > 0; i--)
    {
        int j = rng.Next(i + 1);
        (array[i], array[j]) = (array[j], array[i]);
    }
}

var cardsCopy = (string[])cards.Clone();
ShuffleInPlace(cardsCopy, random);
Console.WriteLine("\nAlternative shuffle:");
Show(cardsCopy);
```

## Ranges 

Using various range approaches:

```csharp
// Basic range using Enumerable.Range
var vals = Enumerable.Range(1, 10);
Console.WriteLine($"From: 1, To: 10");
Console.WriteLine($"[{string.Join(", ", vals)}]");

// Steps using Where with modulo
var vals2 = Enumerable.Range(1, 7).Where(x => x % 2 == 1);
Console.WriteLine($"[{string.Join(", ", vals2)}]"); // [1, 3, 5, 7]

// Reverse range
var vals3 = Enumerable.Range(1, 10).Reverse();
Console.WriteLine($"[{string.Join(", ", vals3)}]");

// Exclusive ranges (equivalent to 1..<10)
var vals4 = Enumerable.Range(1, 9); // Excludes 10
Console.WriteLine($"[{string.Join(", ", vals4)}]");

// Character range
var chars = Enumerable.Range('a', 26).Select(i => (char)i);
Console.WriteLine($"[{string.Join(", ", chars)}]");
Console.WriteLine($"Size: {chars.Count()}");
Console.WriteLine($"Contains 'c': {chars.Contains('c')}");

// Date and time ranges
var months = Enum.GetValues<DayOfWeek>(); // Using enum values
foreach (var month in Enum.GetValues<DateTimeKind>())
{
    // Console.WriteLine(month); // Example with enum
}

// Date range
var startDate = DateTime.Now;
var days = Enumerable.Range(0, 18).Select(i => startDate.AddDays(i));
foreach (var day in days)
{
    Console.WriteLine(day.ToString("yyyy-MM-dd"));
}

// C# 8+ Range operator (limited usage)
int[] array = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
var slice = array[1..^1]; // Excludes first and last elements
Console.WriteLine($"[{string.Join(", ", slice)}]");
```

## Method chaining


Using LINQ method chaining:

```csharp
var vals = new[] {1, 15, 16, 30, 12};

// Filter values between 12 and 18, then sum
var res = vals.Where(x => x >= 12 && x <= 18).Sum();
Console.WriteLine(res); // 43 (15 + 16 + 12)

// Filter values, square them, then sum  
res = vals.Where(x => x != 15 && x != 16).Select(x => x * x).Sum();
Console.WriteLine(res); // 1045 (1² + 30² + 12² = 1 + 900 + 144)
```



## Custom comparation

Using `IComparable` and custom comparers:

```csharp
var words = new[] {"sky", "water", "emotion", "shredder", 
    "anonymous", "on", "a", "copper", "the", "elephant"};

// Sort by length ascending (equivalent to <=>)
var sortedAsc = words.OrderBy(w => w.Length).ToArray();
Console.WriteLine($"[{string.Join(", ", sortedAsc)}]");

// Sort by length descending
var sortedDesc = words.OrderByDescending(w => w.Length).ToArray();
Console.WriteLine($"[{string.Join(", ", sortedDesc)}]");

// Using IComparable<T> interface
public class User : IComparable<User>
{
    public string FirstName { get; set; }
    public string LastName { get; set; }
    public string Occupation { get; set; }

    public User(string firstName, string lastName, string occupation)
    {
        FirstName = firstName;
        LastName = lastName;
        Occupation = occupation;
    }

    public int CompareTo(User? other)
    {
        if (other == null) return 1;
        return string.Compare(LastName, other.LastName, StringComparison.Ordinal);
    }

    public override string ToString()
    {
        return $"{FirstName} {LastName} - {Occupation}";
    }
}

var users = new[]
{
    new User("John", "Doe", "gardener"),
    new User("Roger", "Roe", "driver"),
    new User("Lucia", "Smith", "accountant"),
    new User("Paul", "Newman", "firefighter"),
    new User("Adam", "Clapton", "teacher"),
    new User("Jane", "Walter", "pilot")
};

Console.WriteLine("Original:");
foreach (var user in users)
    Console.WriteLine(user);

Console.WriteLine("\nSorted:");
foreach (var user in users.OrderBy(u => u))
    Console.WriteLine(user);
```

## grepping/filtering  

Using LINQ filtering:

```csharp
// Filter values in range
var res = new[] {1, 15, 16, 30, 12}.Where(x => x >= 12 && x <= 18).ToArray();
Console.WriteLine($"[{string.Join(", ", res)}]"); // [15, 16, 12]

// Filter positive values
var res2 = new[] {1, 2, -1, 0, 2, 3, -3, 4}.Where(x => x > 0).ToArray();
Console.WriteLine($"[{string.Join(", ", res2)}]"); // [1, 2, 2, 3, 4]

// Filter by regex (3 characters)
var words = new[] {"sky", "cloud", "war", "wasp", "water", "coin"};
var res3 = words.Where(w => w.Length == 3).ToArray();
Console.WriteLine($"[{string.Join(", ", res3)}]"); // [sky, war]

// Filter by type
object[] data = {true, "sky", 1.2, 0, new decimal(4), new[] {1, 2, 3}};
var res4 = data.OfType<decimal>().ToArray(); // Filter for decimal numbers
Console.WriteLine($"[{string.Join(", ", res4)}]"); // [4]

// Filter by contains (intersection)
var words2 = new[] {"key", "cup", "cloud", "storm", "wood"};
var filter = new[] {"cup", "wood", "car"};
var res5 = words2.Where(w => filter.Contains(w)).ToArray();
Console.WriteLine($"[{string.Join(", ", res5)}]"); // [cup, wood]
```

Custom GCD with recursion


```csharp
static int Gcd(int a, int b)
{
    return b == 0 ? a : Gcd(b, a % b);
}

// Usage
Console.WriteLine(Gcd(48, 18)); // 6
```

## Filter lines

```csharp
// C# requires explicit return types and parameter types
static int Sum(int x, int y)
{
    return x + y;
}

Console.WriteLine(Sum(1, 3)); // 4

// Using generic method for flexibility
static T Sum<T>(T x, T y) where T : INumber<T>
{
    return x + y;
}
```


## Process


Using `Process` class:

```csharp
using System.Diagnostics;

// Run external program and read output
var process = new Process
{
    StartInfo = new ProcessStartInfo
    {
        FileName = "ls",
        Arguments = "-l",
        RedirectStandardOutput = true,
        UseShellExecute = false,
        CreateNoWindow = true
    }
};

process.Start();
string output = process.StandardOutput.ReadToEnd();
process.WaitForExit();

Console.WriteLine(output);

// Run commands and get output
static string RunCommand(string command, string arguments = "")
{
    var process = new Process
    {
        StartInfo = new ProcessStartInfo
        {
            FileName = command,
            Arguments = arguments,
            RedirectStandardOutput = true,
            UseShellExecute = false,
            CreateNoWindow = true
        }
    };
    
    process.Start();
    string result = process.StandardOutput.ReadToEnd();
    process.WaitForExit();
    return result;
}

Console.WriteLine(RunCommand("dotnet", "--version"));
Console.WriteLine("--------------------------------");
Console.WriteLine(RunCommand("echo", "Hello there!"));
```  

## Records


```csharp
using System;
using System.Linq;

// C# record declaration
record User(string Name, string Occupation, DateTime Dob);

var users = new[]
{
    new User("John Doe", "gardener", DateTime.Parse("1973-09-07")),
    new User("Roger Roe", "driver", DateTime.Parse("1963-03-30")),
    new User("Kim Smith", "teacher", DateTime.Parse("1980-05-12")),
    new User("Joe Nigel", "artist", DateTime.Parse("1983-03-30")),
    new User("Liam Strong", "teacher", DateTime.Parse("2009-03-06")),
    new User("Robert Young", "gardener", DateTime.Parse("1978-11-16")),
    new User("Liam Strong", "teacher", DateTime.Parse("1986-10-23"))
};

// Group by occupation using LINQ
var res = users.GroupBy(u => u.Occupation);

foreach (var group in res)
{
    Console.WriteLine($"{group.Key}: [{string.Join(", ", group.Select(u => u.Name))}]");
}
```



## Find GCD from the max & min in a list 

```csharp
using System.Numerics;

var vals = new[] {8, 5, 10};

var min = new BigInteger(vals.Min());
var max = new BigInteger(vals.Max());

Console.WriteLine(BigInteger.GreatestCommonDivisor(min, max)); // 1

// Using BigInteger directly
var bigVals = new[] {new BigInteger(8), new BigInteger(5), new BigInteger(10)};
var bigMin = bigVals.Min();
var bigMax = bigVals.Max(); 

Console.WriteLine(BigInteger.GreatestCommonDivisor(bigMin, bigMax)); // 1

// For regular integers, you can also use:
static int Gcd(int a, int b) => b == 0 ? a : Gcd(b, a % b);
Console.WriteLine(Gcd(vals.Max(), vals.Min())); // 1
```

## Read file

Using File class methods:

```csharp
// Read file line by line
var lines = File.ReadAllLines("words.txt");
for (int i = 0; i < lines.Length; i++)
{
    Console.WriteLine($"line {i + 1}: {lines[i]}");
}

// Alternative: enumerate lines with index
foreach (var (line, index) in File.ReadLines("words.txt").Select((line, i) => (line, i + 1)))
{
    Console.WriteLine($"line {index}: {line}");
}

// Filter lines that start with 'w'
var filteredLines = File.ReadLines("words.txt")
    .Where(line => line.StartsWith("w"))
    .ToArray();
Console.WriteLine($"[{string.Join(", ", filteredLines)}]");

// Read entire file content
var content = File.ReadAllText("words.txt");
Console.WriteLine(content);

// Read all lines into array
var allLines = File.ReadAllLines("words.txt");
Console.WriteLine($"[{string.Join(", ", allLines)}]");

// Append to file
File.AppendAllText("words.txt", "falcon\nowl\n");
```  


