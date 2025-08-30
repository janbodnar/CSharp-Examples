# C# Lambda Expressions

Lambda expressions in C# provide a concise way to write anonymous functions.  
They are commonly used with delegates, LINQ operations, and expression trees.  
Lambda expressions can replace anonymous methods in most cases with cleaner  
syntax.

## Basic Lambda Expression Syntax

The basic syntax uses the lambda operator `=>`:

```csharp
// Basic lambda expression syntax
// (parameters) => expression
// (parameters) => { statements; }

// Simple lambda with single parameter
Func<int, int> square = x => x * x;
Console.WriteLine(square(5)); // Output: 25

// Lambda with multiple parameters
Func<int, int, int> add = (x, y) => x + y;
Console.WriteLine(add(3, 4)); // Output: 7

// Lambda with statement body
Action<string> greet = name => 
{
    string message = $"Hello, {name}!";
    Console.WriteLine(message);
};
greet("Alice"); // Output: Hello, Alice!
```

## Action Delegates with Lambda Expressions

Action delegates represent methods that return void:

```csharp
// Action<T> - takes one parameter, returns void
Action<string> printMessage = message => Console.WriteLine($"Message: {message}");
printMessage("Lambda expressions are powerful!");

// Action<T1, T2> - takes multiple parameters
Action<string, int> printInfo = (name, age) => 
    Console.WriteLine($"Name: {name}, Age: {age}");
printInfo("Bob", 30);

// Action (no parameters)
Action sayHello = () => Console.WriteLine("Hello World!");
sayHello();

// Using lambda with existing methods
var numbers = new[] { 1, 2, 3, 4, 5 };
Array.ForEach(numbers, x => Console.Write($"{x} "));
Console.WriteLine(); // Output: 1 2 3 4 5
```

## Func Delegates with Lambda Expressions

Func delegates represent methods that return a value:

```csharp
// Func<TResult> - no parameters, returns TResult
Func<DateTime> getCurrentTime = () => DateTime.Now;
Console.WriteLine($"Current time: {getCurrentTime()}");

// Func<T, TResult> - one parameter, returns TResult
Func<double, double> sqrt = x => Math.Sqrt(x);
Console.WriteLine($"Square root of 16: {sqrt(16)}"); // Output: 4

// Func<T1, T2, TResult> - multiple parameters
Func<int, int, string> formatNumbers = (a, b) => $"First: {a}, Second: {b}";
Console.WriteLine(formatNumbers(10, 20));

// More complex lambda with conditional logic
Func<int, string> categorizeNumber = x => x switch
{
    < 0 => "Negative",
    0 => "Zero",
    > 0 and < 10 => "Small positive",
    _ => "Large positive"
};

Console.WriteLine(categorizeNumber(-5)); // Output: Negative
Console.WriteLine(categorizeNumber(3));  // Output: Small positive
```

## Predicate Delegates

Predicate delegates test conditions and return boolean values:

```csharp
// Predicate<T> - takes one parameter, returns bool
Predicate<int> isEven = x => x % 2 == 0;
Predicate<string> isLongWord = word => word.Length > 5;

Console.WriteLine(isEven(4));           // Output: True
Console.WriteLine(isEven(7));           // Output: False
Console.WriteLine(isLongWord("hello")); // Output: False
Console.WriteLine(isLongWord("lambda")); // Output: True

// Using predicates with arrays
var words = new[] { "cat", "dog", "elephant", "mouse", "butterfly" };
var longWords = Array.FindAll(words, isLongWord);
Console.WriteLine($"Long words: [{string.Join(", ", longWords)}]");
// Output: Long words: [elephant, butterfly]

// Combining predicates
Predicate<int> isPositive = x => x > 0;
Predicate<int> isSmall = x => x < 100;
Predicate<int> isPositiveAndSmall = x => isPositive(x) && isSmall(x);

Console.WriteLine(isPositiveAndSmall(50));  // Output: True
Console.WriteLine(isPositiveAndSmall(-10)); // Output: False
```

## Lambda Expressions with LINQ

LINQ heavily uses lambda expressions for querying and transforming data:

```csharp
var numbers = new[] { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
var words = new[] { "apple", "banana", "cherry", "date", "elderberry" };

// Filtering with Where
var evenNumbers = numbers.Where(x => x % 2 == 0).ToArray();
Console.WriteLine($"Even numbers: [{string.Join(", ", evenNumbers)}]");

var longWords = words.Where(w => w.Length > 5).ToArray();
Console.WriteLine($"Long words: [{string.Join(", ", longWords)}]");

// Transformation with Select
var squares = numbers.Select(x => x * x).ToArray();
Console.WriteLine($"Squares: [{string.Join(", ", squares)}]");

var upperWords = words.Select(w => w.ToUpper()).ToArray();
Console.WriteLine($"Upper words: [{string.Join(", ", upperWords)}]");

// Complex queries
var result = numbers
    .Where(x => x > 3)
    .Select(x => new { Number = x, Square = x * x, IsOdd = x % 2 == 1 })
    .Where(item => item.IsOdd)
    .ToArray();

Console.WriteLine("Odd numbers > 3 with their squares:");
foreach (var item in result)
{
    Console.WriteLine($"Number: {item.Number}, Square: {item.Square}");
}
```

## Closures and Variable Capture

Lambda expressions can capture variables from their enclosing scope:

```csharp
// Capturing local variables
int multiplier = 3;
Func<int, int> multiply = x => x * multiplier;
Console.WriteLine(multiply(5)); // Output: 15

// Modifying captured variables
int counter = 0;
Action incrementCounter = () => counter++;
Action printCounter = () => Console.WriteLine($"Counter: {counter}");

incrementCounter();
incrementCounter();
printCounter(); // Output: Counter: 2

// Closure with loop variables (common pitfall)
var actions = new List<Action>();

// Correct way - each lambda captures its own copy
for (int i = 0; i < 3; i++)
{
    int localI = i; // Capture local copy
    actions.Add(() => Console.WriteLine($"Action {localI}"));
}

Console.WriteLine("Executing actions:");
actions.ForEach(action => action());
// Output: Action 0, Action 1, Action 2

// Factory method using closures
static Func<int, int> CreateMultiplier(int factor)
{
    return x => x * factor; // Captures 'factor' parameter
}

var multiplyBy5 = CreateMultiplier(5);
var multiplyBy10 = CreateMultiplier(10);
Console.WriteLine(multiplyBy5(3));  // Output: 15
Console.WriteLine(multiplyBy10(3)); // Output: 30
```

## Expression Trees

Lambda expressions can be converted to expression trees for meta-programming:

```csharp
using System.Linq.Expressions;

// Expression trees allow inspection of lambda structure
Expression<Func<int, bool>> isEvenExpr = x => x % 2 == 0;
Expression<Func<string, int>> getLengthExpr = s => s.Length;

Console.WriteLine($"Expression: {isEvenExpr}");
Console.WriteLine($"Body: {isEvenExpr.Body}");
Console.WriteLine($"Parameter: {isEvenExpr.Parameters[0].Name}");

// Compiling and executing expression trees
var isEvenCompiled = isEvenExpr.Compile();
Console.WriteLine(isEvenCompiled(4)); // Output: True

// Building expression trees programmatically
var parameter = Expression.Parameter(typeof(int), "x");
var constant = Expression.Constant(2);
var modulo = Expression.Modulo(parameter, constant);
var zero = Expression.Constant(0);
var equal = Expression.Equal(modulo, zero);
var lambda = Expression.Lambda<Func<int, bool>>(equal, parameter);

var compiledExpression = lambda.Compile();
Console.WriteLine($"Programmatic expression result: {compiledExpression(6)}");
```

## Event Handling with Lambda Expressions

Lambda expressions simplify event handling:

```csharp
// Simple event handler simulation
class EventPublisher
{
    public event Action<string> SomethingHappened;
    
    public void TriggerEvent(string message)
    {
        SomethingHappened?.Invoke(message);
    }
}

var publisher = new EventPublisher();

// Subscribe with lambda expressions
publisher.SomethingHappened += message => 
    Console.WriteLine($"Handler 1: {message}");
    
publisher.SomethingHappened += message => 
    Console.WriteLine($"Handler 2: {message.ToUpper()}");

publisher.TriggerEvent("Hello Event!");
// Output: Handler 1: Hello Event!
//         Handler 2: HELLO EVENT!

// Generic event handling
class GenericEventPublisher<T>
{
    public event Action<T> DataReceived;
    
    public void PublishData(T data)
    {
        DataReceived?.Invoke(data);
    }
}

var intPublisher = new GenericEventPublisher<int>();
intPublisher.DataReceived += value => 
    Console.WriteLine($"Received integer: {value}");
intPublisher.PublishData(42);
```

## Practical Examples

### Functional Programming Style Operations

```csharp
// Chain of operations using lambda expressions
var numbers = Enumerable.Range(1, 20);

var result = numbers
    .Where(x => x % 2 == 0)           // Even numbers only
    .Select(x => x * x)               // Square them
    .Where(x => x > 50)               // Keep large squares
    .OrderByDescending(x => x)        // Sort descending
    .Take(3)                          // Take top 3
    .ToList();

Console.WriteLine($"Top 3 large even squares: [{string.Join(", ", result)}]");

// Custom sorting with lambda expressions
var people = new[]
{
    new { Name = "Alice", Age = 30, City = "New York" },
    new { Name = "Bob", Age = 25, City = "London" },
    new { Name = "Charlie", Age = 35, City = "Tokyo" },
    new { Name = "Diana", Age = 28, City = "Paris" }
};

// Multiple sorting criteria
var sortedPeople = people
    .OrderBy(p => p.City)           // Primary sort by city
    .ThenByDescending(p => p.Age)   // Secondary sort by age (descending)
    .ToList();

Console.WriteLine("Sorted people:");
sortedPeople.ForEach(p => 
    Console.WriteLine($"{p.Name}, {p.Age}, {p.City}"));
```

### Data Transformation Pipeline

```csharp
// Complex data transformation using lambda expressions
var salesData = new[]
{
    new { Product = "Laptop", Price = 1200, Quantity = 2, Category = "Electronics" },
    new { Product = "Mouse", Price = 25, Quantity = 10, Category = "Electronics" },
    new { Product = "Book", Price = 15, Quantity = 5, Category = "Education" },
    new { Product = "Pen", Price = 2, Quantity = 50, Category = "Office" },
    new { Product = "Monitor", Price = 300, Quantity = 3, Category = "Electronics" }
};

// Calculate total revenue by category
var revenueByCategory = salesData
    .GroupBy(item => item.Category)
    .Select(group => new
    {
        Category = group.Key,
        TotalRevenue = group.Sum(item => item.Price * item.Quantity),
        ItemCount = group.Count(),
        AverageItemPrice = group.Average(item => item.Price)
    })
    .OrderByDescending(summary => summary.TotalRevenue)
    .ToList();

Console.WriteLine("Revenue by Category:");
revenueByCategory.ForEach(summary =>
    Console.WriteLine($"{summary.Category}: ${summary.TotalRevenue} " +
                     $"({summary.ItemCount} items, avg price: ${summary.AverageItemPrice:F2})"));
```

### Memoization with Lambda Expressions

```csharp
// Memoization pattern using lambda expressions and closures
static Func<T, TResult> Memoize<T, TResult>(Func<T, TResult> function)
{
    var cache = new Dictionary<T, TResult>();
    return argument =>
    {
        if (cache.TryGetValue(argument, out TResult cachedResult))
        {
            Console.WriteLine($"Cache hit for {argument}");
            return cachedResult;
        }
        
        Console.WriteLine($"Computing result for {argument}");
        var result = function(argument);
        cache[argument] = result;
        return result;
    };
}

// Example: Expensive Fibonacci calculation with memoization
Func<int, long> fibonacci = null;
fibonacci = Memoize<int, long>(n => n <= 1 ? n : fibonacci(n - 1) + fibonacci(n - 2));

Console.WriteLine($"Fibonacci(10) = {fibonacci(10)}");
Console.WriteLine($"Fibonacci(10) = {fibonacci(10)}"); // This will use cache
```

## Performance Considerations

Lambda expressions have performance implications to consider:

```csharp
// Delegate allocation performance
var numbers = Enumerable.Range(1, 1000000);

// Multiple allocations (less efficient)
var result1 = numbers
    .Where(x => x > 500000)
    .Select(x => x * 2)
    .Where(x => x % 3 == 0)
    .Count();

// Optimized approach - combine conditions
var result2 = numbers
    .Where(x => x > 500000 && (x * 2) % 3 == 0)
    .Count();

// For hot paths, consider caching delegates
Func<int, bool> isLargeAndDivisible = x => x > 500000 && (x * 2) % 3 == 0;
var result3 = numbers.Where(isLargeAndDivisible).Count();

Console.WriteLine($"Results: {result1}, {result2}, {result3}");

// Closure allocation considerations
static void DemonstrateClosurePerformance()
{
    var actions = new List<Action>();
    
    // Each lambda captures different variables - multiple closures
    for (int i = 0; i < 5; i++)
    {
        int captured = i;
        actions.Add(() => Console.WriteLine($"Value: {captured}"));
    }
    
    // Better for performance - single shared closure
    var sharedActions = new List<Action>();
    for (int i = 0; i < 5; i++)
    {
        int index = i;
        sharedActions.Add(CreateAction(index));
    }
    
    static Action CreateAction(int value)
    {
        return () => Console.WriteLine($"Value: {value}");
    }
}
```

## Summary

Lambda expressions in C# provide a powerful and concise syntax for functional  
programming patterns. They work seamlessly with delegates, LINQ, and expression  
trees, enabling elegant solutions to complex problems. Key points to remember:  

- Use `=>` operator to separate parameters from expression or statement body  
- Leverage Action, Func, and Predicate delegates for different scenarios    
- LINQ operations heavily utilize lambda expressions for data querying  
- Be mindful of closure captures and their performance implications  
- Expression trees allow meta-programming and dynamic query construction  
- Lambda expressions enable functional programming styles in C#  
