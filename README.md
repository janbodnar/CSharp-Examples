# CSharp-Examples
C# Examples

# Groovy-Examples
Groovy code examples

`println System.getProperty("user.dir")` print current working directory  
`println "ls -la".execute().text` execute shell command  

C# equivalents:
```csharp
Console.WriteLine(Environment.CurrentDirectory); // print current working directory

// Execute shell command
var result = Process.Start(new ProcessStartInfo("ls", "-la") 
{ 
    RedirectStandardOutput = true, 
    UseShellExecute = false 
});
result.WaitForExit();
Console.WriteLine(result.StandardOutput.ReadToEnd());
```

```groovy
def isOdd = { int i -> (i & 1) as boolean }
def isEven = {int i -> ! isOdd(i) }
```
even/odd  

`def evens = [1, 2, 3, 4, 5].findAll{ it % 2 == 0 }` - filter out even values  

C# equivalents:
```csharp
// Lambda functions for odd/even
Func<int, bool> isOdd = i => (i & 1) == 1;
Func<int, bool> isEven = i => !isOdd(i);

// Filter even values using LINQ
var evens = new[] {1, 2, 3, 4, 5}.Where(it => it % 2 == 0).ToArray();
Console.WriteLine($"[{string.Join(", ", evens)}]"); // [2, 4]
```  

## Debug macros (Groovy-specific - skipped)

```groovy
def name = 'John Doe'
def vals = [1, 2, 3, -4, 5]
def words = ['game', 'cup', 'water'] as String[]
def r = 1..10

println SV(name, vals, words, r)
println SVI(name, vals, words, r)

println NV(r)
println NVL(r)
```

*Note: Debug macros like SV(), SVI(), NV(), NVL() are Groovy-specific and don't have direct C# equivalents. In C# debugging, you would typically use debugger tools, Console.WriteLine, or logging frameworks like Serilog or NLog.*

## Executable JARs in Gradle 

```groovy
jar {
  manifest {
    attributes(
      'Main-Class': 'com.zetcode.Application'
    )
  }
}
```

C# equivalent - Creating executable applications with dotnet:

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

## def keyword

With `def` variables act like they are of type Object, so they can be reassigned to different types.  

```groovy
def x = 12
println x.getClass().getName()

x = 'falcon'
println x.getClass().getName()
```

C# equivalent using `var` for type inference and `object` for dynamic typing:

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

```groovy
println System.getProperty("java.vendor")
println System.getProperty("os.arch")
println System.getProperty("os.name")
println System.getProperty("java.class.version")
println System.getProperty("java.class.path")

println System.currentTimeMillis()
```

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

```groovy
println System.getenv("JAVA_HOME")
println System.getenv("GROOVY_HOME")
println System.getenv("PATH")

println '------------------------'

def env = System.getenv().collect { k, v -> "$k=$v" }
env.each { e -> println e }
```

C# equivalent using Environment class:

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

```groovy
def (name1, name2, name3) = ['John Doe', 'Roger Roe', 'Lucia Smith']
println name1 
println name2
println name3
```

Using typed variables on the left side.  

```groovy
def (int x, int y , String w) = [10, 20, 'falcon']

println x
println y
println w
```

The `_` discard operator  

```groovy
def (_, month, year) = "3rd August 2023".split()
println month
println year
```

C# equivalent using tuple deconstruction:

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


## Primitive types are auto-wrapped

```groovy
int n = 3
println n.getClass().getName()
println n.getClass().isPrimitive()

float m = 4.4;
println m.getClass().getName()
println m.getClass().isPrimitive()
```

C# equivalent demonstrating boxing and value types:

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

## Import Groovy code in script (Groovy-specific - skipped)

```groovy
package com.zetcode 

// User.groovy
record User(String name) {}
```

```groovy
package com.zetcode

// main.groovy
this.class.classLoader.parseClass("User.groovy")

def u = new User('John Doe')
println u
```

Run the app `$ groovy com\zetcode\main.groovy`  

*Note: This is specific to Groovy's dynamic class loading. In C#, you would use assemblies, namespaces, and standard project references or dynamic compilation with Roslyn if needed.*  

## Steps

```groovy
1.step(4, 0.5) { print "$it "}
println "\n-----------------------"

1.step(10, 1) { 
    
    println it
}
```

C# equivalent using custom step methods:

```csharp
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
```

## Pick random element from list

```groovy
def words = ["sky", "cup", "tall", "falcon", "cloud"]

def rnd = new Random()

def ri = rnd.nextInt(words.size())
println words[ri]
```

C# equivalent:

```csharp
var words = new[] {"sky", "cup", "tall", "falcon", "cloud"};

var rnd = new Random();

var ri = rnd.Next(words.Length);
Console.WriteLine(words[ri]);

// Alternative using LINQ (more concise)
var randomWord = words.OrderBy(x => rnd.Next()).First();
Console.WriteLine(randomWord);
```


## Unix pipes (Groovy-specific - skipped)

```groovy
def p = 'ls -l'.execute()  | ['awk', '{ print $1, $NF }'].execute()
p.waitFor()
println p.text
```

*Note: Groovy's native pipe operator for processes doesn't have a direct C# equivalent. In C#, you would need to use ProcessStartInfo with RedirectStandardOutput/Input to chain processes manually.*

## Download image

```groovy
import java.nio.file.Files
import java.nio.file.Paths

def data = "http://webcode.me/favicon.ico".toURL().bytes
Files.write(Paths.get('favicon.ico'), data)
```

C# equivalent using HttpClient:

```csharp
using var httpClient = new HttpClient();
var data = await httpClient.GetByteArrayAsync("http://webcode.me/favicon.ico");
await File.WriteAllBytesAsync("favicon.ico", data);

// Synchronous version
var dataSync = httpClient.GetByteArrayAsync("http://webcode.me/favicon.ico").Result;
File.WriteAllBytes("favicon.ico", dataSync);
```

## Iterate runes

```groovy
import java.text.BreakIterator

def text = "🐜🐬🐄🐘🦂🐫🐑🦍🐯🐞"

def it = BreakIterator.getCharacterInstance()
it.setText(text)

def start = it.first()
def end = it.next()

while (start < end) { 

    println(text.substring(start, end))
    start = end 
    end = it.next()
}
```

C# equivalent using StringInfo or direct string enumeration:

```csharp
using System.Globalization;

var text = "🐜🐬🐄🐘🦂🐫🐑🦍🐯🐞";

// Method 1: Using StringInfo
var stringInfo = new StringInfo(text);
for (int i = 0; i < stringInfo.LengthInTextElements; i++)
{
    Console.WriteLine(stringInfo.SubstringByTextElements(i, 1));
}

// Method 2: Using TextElementEnumerator  
var enumerator = StringInfo.GetTextElementEnumerator(text);
while (enumerator.MoveNext())
{
    Console.WriteLine(enumerator.Current);
}

// Method 3: Using Rune (C# 8+)
foreach (var rune in text.EnumerateRunes())
{
    Console.WriteLine(rune.ToString());
}
```

## Create a deck of cards

```groovy
def signs = (2..10) + ['J', 'Q', 'K', 'A']
def symbols = ['♣', '♦', '♥', '♠']
 
// [♣2, ♦2, ♥2, ♠2, ..., ♣A, ♦A, ♥A, ♠A]
def cards = [symbols, signs].combinations().collect { it.join() }
println cards

cards.shuffle()

println cards.take(5)
```

C# equivalent using LINQ for combinations:

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

```groovy

def cards = [
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
]

def show(cards) {

    cards.eachWithIndex { e, i -> 

        if (i != 0 && i % 13 == 0) {
            print "\n"
        }

        print "${e} "
    }

    print "\n"
}


cards.shuffle()
show(cards)
```

C# equivalent with emoji cards and display function:

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

```groovy
import java.time.LocalDate
import java.time.Month

def vals = 1..10
println vals.from
println vals.to
println vals.toList()

// steps
def vals2 = (1..7).step(2)
println vals2

// reverse range
def vals3 = 10..1
println vals3

// exclusive ranges
def vals4 = 1..<10
println vals4.toList()

def vals5 = 1<..<10
println vals5.toList()

def chars = 'a'..'z'
println chars 
println chars.size()
println chars.contains('c')
println chars.getFrom() 
println chars.getTo()

// date & time 
def months = Month.JANUARY..Month.DECEMBER

for (def m in months) {

    println m
}

def days = LocalDate.now()..LocalDate.now().plusDays(17)

for (def d in days) {
    
    println d
}
```

C# equivalent using various range approaches:

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

Groovy has support for method chaining.  

```groovy
int[] vals = [1, 15, 16, 30, 12]

def res = vals.grep(12..18).sum()
println res

res = vals.grep { it != 15 || it != 16 }.collect { it * it }.sum()
println res
```

C# equivalent using LINQ method chaining:

```csharp
var vals = new[] {1, 15, 16, 30, 12};

// Filter values between 12 and 18, then sum
var res = vals.Where(x => x >= 12 && x <= 18).Sum();
Console.WriteLine(res); // 43 (15 + 16 + 12)

// Filter values, square them, then sum  
res = vals.Where(x => x != 15 && x != 16).Select(x => x * x).Sum();
Console.WriteLine(res); // 1045 (1² + 30² + 12² = 1 + 900 + 144)
```

## Spaceship operator 

```groovy
def words = ['sky', 'water', 'emotion', 'shredder', 
    'anonymous', 'on', 'a', 'copper', 'the', 'elephant']

words.sort { e1, e2 -> e1.length() <=> e2.length() }
println words

words.sort { e1, e2 -> e2.length() <=> e1.length() }
println words
```


```groovy
class User implements Comparable {

    String fname
    String lname
    String occupation

    User(String fname, String lname, String occupation) {
        this.fname = fname;
        this.lname = lname;
        this.occupation = occupation;
    }

    int compareTo(o) {
        this.lname <=> o.lname
    }

    String toString() {
        "${this.fname} ${this.lname} - ${this.occupation}"
    }
}


def users = [
    new User('John', 'Doe', 'gardener'),
    new User('Roger', 'Roe', 'driver'),
    new User('Lucia', 'Smith', 'accountant'),
    new User('Paul', 'Newman', 'firefighter'),
    new User('Adam', 'Clapton', 'teacher'),
    new User('Jane', 'Walter', 'pilot')
]

println users
println users.sort()
```

C# equivalent using IComparable and custom comparers:

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

```groovy
def res = [1, 15, 16, 30, 12].grep(12..18)
println res

def res2 = [1, 2, -1, 0, 2, 3, -3, 4].grep({it > 0})
println res2

def words = ['sky', 'cloud', 'war', 'wasp', 'water', 'coin']
def res3 = words.grep(~/.../)
println res3
```

Filter by class and list contains

```groovy
def data = [true, 'sky', 1.2, 0, 1..3, new BigDecimal(4), [1, 2, 3]]

def res = data.grep(Number)
println(res)

def words = ['key', 'cup', 'cloud', 'storm', 'wood']
res = words.grep(['cup', 'wood', 'car'])
println res
```

C# equivalent using LINQ filtering:

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


```groovy
def gcd(a,b) {
  if (!b) a
  else gcd(b, a%b)
}
```
Custom GCD with recursion

C# equivalent:

```csharp
static int Gcd(int a, int b)
{
    return b == 0 ? a : Gcd(b, a % b);
}

// Usage
Console.WriteLine(Gcd(48, 18)); // 6
```

## Filter lines

```groovy
def fname = 'words.txt'
def f = new File(fname)

// def res = f.filterLine { it =~ /^w.*/ }
def res = f.filterLine { it =~ /^w.*/ }
println res
```

## Methods must return def or type

```groovy
sum(x, y) {
    x + y
}

println sum(1, 3)
```

This code fails.

C# equivalent showing proper method declaration:

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

```groovy
def process = "ls -l".execute()

process.in.eachLine { line ->
    println line
}
```
Runs external program

```groovy
def c1 = "perl --version"
def c2 = "perl -e 'system(\"echo Hello there!\")'"

println c1.execute().text
println "--------------------------------"
println c2.execute().text
```
Runs Perl one liners  

C# equivalent using Process class:

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

## Grouping

```groovy
import java.time.LocalDate
import groovy.transform.Immutable

@Immutable
class User {
    String name
    String occupation
    LocalDate dob
}
 
def users = [

    new User('John Doe', 'gardener', LocalDate.parse('1973-09-07', 'yyyy-MM-dd')),
    new User('Roger Roe', 'driver', LocalDate.parse('1963-03-30', 'yyyy-MM-dd')),
    new User('Kim Smith', 'teacher', LocalDate.parse('1980-05-12', 'yyyy-MM-dd')),
    new User('Joe Nigel', 'artist', LocalDate.parse('1983-03-30', 'yyyy-MM-dd')),
    new User('Liam Strong', 'teacher', LocalDate.parse('2009-03-06', 'yyyy-MM-dd')),
    new User('Robert Young', 'gardener', LocalDate.parse('1978-11-16', 'yyyy-MM-dd')),
    new User('Liam Strong', 'teacher', LocalDate.parse('1986-10-23', 'yyyy-MM-dd'))
]
 
def res = users.groupBy({ it.occupation })

for (e in res) {
    println e
}
```

Group data by occupation

## Records 

Groovy 4 introduced records  

```groovy
import java.time.LocalDate

record User(String name, String occupation, LocalDate dob) { }

def users = [

    new User('John Doe', 'gardener', LocalDate.parse('1973-09-07', 'yyyy-MM-dd')),
    new User('Roger Roe', 'driver', LocalDate.parse('1963-03-30', 'yyyy-MM-dd')),
    new User('Kim Smith', 'teacher', LocalDate.parse('1980-05-12', 'yyyy-MM-dd')),
    new User('Joe Nigel', 'artist', LocalDate.parse('1983-03-30', 'yyyy-MM-dd')),
    new User('Liam Strong', 'teacher', LocalDate.parse('2009-03-06', 'yyyy-MM-dd')),
    new User('Robert Young', 'gardener', LocalDate.parse('1978-11-16', 'yyyy-MM-dd')),
    new User('Liam Strong', 'teacher', LocalDate.parse('1986-10-23', 'yyyy-MM-dd'))
]
 
def res = users.groupBy({ it.occupation })

for (e in res) {
    
    println e
}
```

C# equivalent using records (C# 9+):

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

```groovy
def vals = [8, 5, 10]

def min = vals.min() as BigInteger
def max = vals.max() as BigInteger

println min.gcd(max)
```
Casting to BigInteger

```groovy
def vals = [8g, 5g, 10g]

def min = vals.min()
def max = vals.max()

println min.gcd(max)
```
Using BigInteger literals

C# equivalent using System.Numerics.BigInteger:

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

## Read CSV file

```groovy
@Grab(group='com.opencsv', module='opencsv', version='5.5.2')

import java.nio.file.Files
import java.nio.file.Paths
import com.opencsv.CSVParserBuilder
import com.opencsv.CSVReaderBuilder

def fname = 'src/resources/cars.csv'
def br = Files.newBufferedReader(Paths.get(fname))

def parser = new CSVParserBuilder().withSeparator(',' as char).build()
def reader = new CSVReaderBuilder(br).withCSVParser(parser).build()

def lines = reader.readAll()

for (line in lines) {
    println line.join(" ")
}
```
reads CSV file with OpenCSV library

## Convert CSV file to HTML table

```groovy
package com.zetcode

@Grab(group='org.codehaus.groovy', module='groovy-xml', version='3.0.9')
@Grab(group='com.opencsv', module='opencsv', version='5.5.2')

import java.nio.file.Files
import java.nio.file.Paths
import com.opencsv.CSVParserBuilder
import com.opencsv.CSVReaderBuilder
import groovy.xml.MarkupBuilder

def fname = 'cars.csv'
def br = Files.newBufferedReader(Paths.get(fname))

def parser = new CSVParserBuilder().withSeparator(',' as char).build()
def reader = new CSVReaderBuilder(br).withCSVParser(parser).build()

def lines = reader.readAll()

def buildTable(rows, n) {
    
    def sw = new StringWriter()
    
    new MarkupBuilder(sw).table() {
        thead {
            tr {
                rows[0].each { f -> th(f)}
            }
        } 
        tbody {
            (1..n).each { row ->
                tr {
                    rows[row].each { f -> td(f) }
                }
            }
        }
    }
    
    sw.toString()
}

println buildTable(lines.toList(), lines.size()-1)
```

## Parse XML

```groovy
import groovy.xml.XmlSlurper

def data = '''<?xml version="1.0" encoding="utf-8"?>
<products>
    <product>
        <id>1</id>
        <name>Product A</name>
        <price>780</price>
    </product>

    <product>
        <id>2</id>
        <name>Product B</name>
        <price>1100</price>
    </product>

    <product>
        <id>3</id>
        <name>Product C</name>
        <price>1050</price>
    </product>

    <product>
        <id>4</id>
        <name>Product D</name>
        <price>950</price>
    </product>
</products>
'''

def products = new XmlSlurper().parseText(data)

def id1 = products.product[0].id
def name1 = products.product[0].name
def price1 = products.product[0].price

println "$id1 $name1 $price1"

def names = products.'**'.findAll { node -> node.name() == 'name' }*.text()
println names

def prices = products.product.'*'.find { node ->

    node.name() == 'price' && node.text() as Integer < 1000
}

print prices
```


## Iterate over lines of URL

```groovy
def url = new URL("http://www.webcode.me")

url.eachLine { println it }
```

## Socket HEAD/GET request

```groovy
def s = new Socket("webcode.me", 80)

s.withStreams { sin, sout ->
  
  sout << "HEAD / HTTP/1.1\r\nConnection: close\r\nHost: webcode.me\r\nAccept: text/html\r\n\r\n" 
  
  def reader = sin.newReader()
  def lines = reader.readLines()
  
  for (line in lines) {
      println line
  }
}
```

```groovy
def host = "webcode.me"
int port = 80

def s = new Socket(host, port)

s.setSoTimeout(18000)

s.withStreams { sin, sout ->

    sout << "GET / HTTP/1.1\r\n"
    sout << "Connection: close\r\n"
    sout << "Host: www.webcode.me\r\n\r\n"

    def text = sin.text
    println text
}
```

## Web scraping with JSoup  

```groovy
@Grab(group='org.jsoup', module='jsoup', version='1.10.1')
import org.jsoup.Jsoup

def doc = Jsoup.connect("http://webcode.me").get()
def title = doc.select('title')
def elements = doc.select('*')

println doc
println title

elements.each { e ->
    println e
}
```

## Files

```groovy
def f = new File("words.txt")

f.eachLine { ln, n ->
    println "line $n: $ln"
}
```
Read file line by line

---

```groovy
def fname = 'src/resources/words.txt'
def f = new File(fname)

def res = f.filterLine { it =~ /^w.*/ }
println res
```
filter lines; include only that start with 'w'

---

```groovy
def fname = 'words.txt'
def f = new File(fname)

println f.text 
```
read contents

---

```groovy
def fname = 'words.txt'
def f = new File(fname)

// def lines = f as String[]
// println lines

def lines = f.readLines()
println lines
```
read lines into list

---

```groovy
def fname = 'words.txt'
def f = new File(fname)

f.withWriterAppend('utf-8') {
	writer -> writer.append('falcon\n').append('owl')
}
```
append to file  

C# equivalent using File class methods:

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

## Undertow server 

```groovy
package com.zetcode

@Grab(group='io.undertow', module='undertow-core', version='2.3.7.Final')

import io.undertow.Undertow
import io.undertow.util.Headers

def server = Undertow.builder()
        .addHttpListener(8080, "localhost")
        .setHandler(exchange -> {
            exchange.getResponseHeaders().put(Headers.CONTENT_TYPE, "text/plain")
            exchange.getResponseSender().send("Hello there")
        }).build()

server.start()
```

## Working with H2 in-memory database

```groovy
@GrabConfig(systemClassLoader=true)
@Grab(group='com.h2database', module='h2', version='1.4.200')

import groovy.sql.Sql

def createTable = '''
CREATE TABLE cars(id INT PRIMARY KEY AUTO_INCREMENT, name VARCHAR(255), price INT);
INSERT INTO cars(name, price) VALUES('Audi', 52642);
INSERT INTO cars(name, price) VALUES('Mercedes', 57127);
INSERT INTO cars(name, price) VALUES('Skoda', 9000);
INSERT INTO cars(name, price) VALUES('Volvo', 29000);
INSERT INTO cars(name, price) VALUES('Bentley', 350000);
INSERT INTO cars(name, price) VALUES('Citroen', 21000);
INSERT INTO cars(name, price) VALUES('Hummer', 41400);
INSERT INTO cars(name, price) VALUES('Volkswagen', 21600);
'''

def url = "jdbc:h2:mem:"
def sql = Sql.withInstance(url) { sql ->

    sql.execute("DROP TABLE IF EXISTS cars")
    sql.execute(createTable)

    def query = "SELECT * FROM cars"

    sql.eachRow(query) { row ->
      println "$row.id  ${row.name} $row.price"
    }
}
```

## Fetch all rows from db  

```groovy
@Grab(group='org.postgresql', module='postgresql', version='42.2.24')
@GrabConfig(systemClassLoader=true)

import groovy.sql.Sql

def url = 'jdbc:postgresql://localhost:5432/testdb'
def user = 'postgres'
def password = ''
def driver = 'org.postgresql.Driver'

Sql.withInstance(url, user, password, driver) { sql ->

    def res = sql.rows('SELECT * FROM cars')
    println res
}
```

## Find all text files  

```groovy
import static groovy.io.FileType.FILES

def f = new File('/home/jano7/Documents')

f.eachFileRecurse(FILES) {
    if(it.name.endsWith('.txt')) {
        println it
    }
}
```

```groovy
import static groovy.io.FileType.FILES

def f = new File('/home/jano7/Documents')

f.traverse(type: FILES, nameFilter: ~/.*.txt/) { it ->
	println it
}
```

The *nameFilter* is an exact match   

## Iterate over range of datetime values

```groovy
@Grab('org.codehaus.groovy:groovy-datetime:3.0.9')

import java.time.Instant
import java.time.temporal.ChronoUnit

def now = Instant.now()
println now

def d2 = now.plus(3, ChronoUnit.DAYS)

println "--------------"

now.upto(d2, ChronoUnit.DAYS) {
	
	println it
}
```

## SFTP list directory

```groovy
@Grab(group='com.hierynomus', module='sshj', version='0.35.0')

import net.schmizz.sshj.SSHClient
import net.schmizz.sshj.transport.verification.PromiscuousVerifier
import net.schmizz.sshj.sftp.SFTPClient
import net.schmizz.sshj.sftp.RemoteResourceInfo

try {

    def client = new SSHClient()

    client.addHostKeyVerifier(new PromiscuousVerifier())
    client.connect("hostname")
    client.authPassword("username", "s$cret")
    
    SFTPClient sftp = client.newSFTPClient()

    List<RemoteResourceInfo> resourceInfoList = sftp.ls("/web/perl/")

    for (def e : resourceInfoList) {
        println(e.getName())
    }

} finally {
    sftp.close() 
    client.disconnect()
}
```


## TableSaw dataframe 

```groovy
package com.zetcode

@Grab(group='tech.tablesaw', module='tablesaw-core', version='0.41.0')
@Grab(group='org.slf4j', module='slf4j-simple', version='1.7.32', scope='test')

import tech.tablesaw.api.Table
import static tech.tablesaw.aggregate.AggregateFunctions.min
import static tech.tablesaw.aggregate.AggregateFunctions.max
import static tech.tablesaw.aggregate.AggregateFunctions.mean
import static tech.tablesaw.aggregate.AggregateFunctions.median
import static tech.tablesaw.aggregate.AggregateFunctions.count

def tbl = Table.read().csv("src/resources/cars.csv")

println tbl.shape()
println '---------------------------'

println tbl.structure()
println '---------------------------'

println tbl.first(3)
println '---------------------------'

println tbl.last(2)
println '---------------------------'

println tbl.column('price').min()
println tbl.column('price').max()
println tbl.column('price').asList()

println tbl.where { it.numberColumn(2).isGreaterThan(50_000) }
println tbl.where { it.numberColumn(2).isLessThan(25_000) }.rowCount()

println '---------------------------'

def price = tbl.nCol('price')
println tbl.summarize(price, count, max, min, mean, median).apply()

println '---------------------------'

println tbl.select("name", "price")


println '---------------------------'
println tbl.sampleN(4)

println '---------------------------'

println tbl.sortAscendingOn("price")
```


## Playwright  

Browser automation with Playwright  

```groovy
@Grab(group='com.microsoft.playwright', module='playwright', version='1.19.0')

import com.microsoft.playwright.Playwright

Playwright.create().withCloseable { client -> 

    def browser = client.chromium().launch()

    def page = browser.newPage()

    page.navigate("http://webcode.me")
    println page.title()
}
```

## Generate test data 

Generating test data with `datafaker`.  

```groovy
@Grab(group='net.datafaker', module='datafaker', version='2.0.1')

import net.datafaker.Faker

import java.util.concurrent.TimeUnit

def faker = new Faker()

println faker.name().fullName()

String firstName = faker.name().firstName()
String lastName = faker.name().lastName()
println "${firstName} ${lastName}"

println faker.address().streetAddress()

println faker.job().title()
println faker.job().position()

println faker.country().name()
println faker.country().capital()

println faker.date().birthday()
println faker.date().birthday('Y/M/d')
println faker.date().birthday(18, 65)
println faker.date().future(30, TimeUnit.DAYS)
```



## Groovy template engine

### Simple

```groovy
import groovy.text.SimpleTemplateEngine

def text = 'Hello $name!'

def ctx = ["name": "John Doe"]

def engine = new SimpleTemplateEngine() 
def res = engine.createTemplate(text).make(ctx)

println res
```

### From file

```jsp
${name} is a ${occupation}
```

This is `message.txt` file.

```groovy
import groovy.text.SimpleTemplateEngine

def text = new File("message.txt").text
def ctx = ["name": "John Doe", "occupation": "gardener"]

def engine = new SimpleTemplateEngine() 
def res = engine.createTemplate(text).make(ctx)

println res
```

### Loop 

```groovy
import groovy.text.SimpleTemplateEngine

def words = [ "sky", "blue", "cran", "cotton", "wood" ]

def ctx = [words: words]

def engine = new SimpleTemplateEngine()
def text = '''<% words.each { println "${it} has ${it.length()} characters" } %>'''

def res = engine.createTemplate(text).make(ctx)
println res
```

### Records

```groovy
import groovy.text.SimpleTemplateEngine

record User(String name, String occupation) {}

def text = '<% users.each { println "${it.name} is a ${it.occupation}" } %>'

def users = [ 
    new User("John Doe", "gardener"), new User("Roger Roe", "driver"), 
    new User("Peter Smith", "teacher")
]

def ctx = [users: users]

def engine = new SimpleTemplateEngine()

def res = engine.createTemplate(text).make(ctx)
println res
```

### If condition

```jsp
<% for (task in tasks) { %>
    <% if (task.done) { %>
        <%= task.title %>
    <% } %>
<% } %>
```

```groovy
import groovy.text.SimpleTemplateEngine
import groovy.transform.Immutable

@Immutable
class Task {
    String title
    boolean done
}

def text = new File("tasks.txt").text

def tasks = [ 
    new Task("Task 1", true), new Task("Task 2", true), 
    new Task("Task 3", false), new Task("Task 4", true), 
    new Task("Task 5", false) 
]

def ctx = ["tasks": tasks]

def engine = new SimpleTemplateEngine()

def res = engine.createTemplate(text).make(ctx)
def out = res.toString()

println out.replaceAll("\s{2,}", "").replaceAll("\n{2,}", "\n").strip()
```


## Jinjava template engine

```jinja
{%- for task in tasks -%}
    {% if task.done %}
        {{ task.title }}
    {% endif %}
{%- endfor %}
```
This is `tasks.jinja` template file.

```groovy
@Grab(group='com.hubspot.jinjava', module='jinjava', version='2.6.0')

import com.hubspot.jinjava.Jinjava
import groovy.transform.Immutable

@Immutable
class Task {
    String title
    boolean done
}

def jnj = new Jinjava()

def tasks = [ new Task("Task 1", true),
    new Task("Task 2", true), new Task("Task 3", false),
    new Task("Task 4", true), new Task("Task 5", false) ]

def context = ["tasks": tasks]

def fileName = "tasks.jinja"
def template = new File(fileName).text

def res = jnj.render(template, context)
println res

// record Task(String title, boolean done) { }
```

Records are not working, we use `@Immutable` instead.  


