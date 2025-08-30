# C# Arrays

This tutorial covers C# arrays - ordered collections of elements of the same type. Arrays are fundamental data structures in C# that allow you to store multiple values in a single variable.

## Array Declaration and Initialization

Arrays can be declared and initialized in several ways:

```csharp
// Declaration and initialization with size
int[] numbers = new int[5];

// Declaration and initialization with values
int[] values = {1, 2, 3, 4, 5};

// Alternative syntax with new keyword
int[] data = new int[] {10, 20, 30, 40, 50};

// Array initialization with specific size and default values
string[] names = new string[3]; // Contains null values

// Mixed declaration and assignment
double[] prices;
prices = new double[] {19.99, 29.95, 39.50};

Console.WriteLine($"numbers array length: {numbers.Length}");
Console.WriteLine($"values: [{string.Join(", ", values)}]");
Console.WriteLine($"data: [{string.Join(", ", data)}]");
Console.WriteLine($"prices: [{string.Join(", ", prices)}]");
```

## Accessing Array Elements

Array elements are accessed using zero-based indexing:

```csharp
string[] colors = {"red", "green", "blue", "yellow", "purple"};

// Accessing elements by index
Console.WriteLine($"First color: {colors[0]}");
Console.WriteLine($"Third color: {colors[2]}");
Console.WriteLine($"Last color: {colors[colors.Length - 1]}");

// Modifying array elements
colors[1] = "orange";
Console.WriteLine($"Modified array: [{string.Join(", ", colors)}]");

// Using indices and ranges (C# 8.0+)
Console.WriteLine($"First three: [{string.Join(", ", colors[0..3])}]");
Console.WriteLine($"Last two: [{string.Join(", ", colors[^2..])}]");
```

## Array Properties and Methods

Arrays have useful properties and methods:

```csharp
int[] numbers = {5, 2, 8, 1, 9, 3};

Console.WriteLine($"Array length: {numbers.Length}");
Console.WriteLine($"Original: [{string.Join(", ", numbers)}]");

// Sorting array
Array.Sort(numbers);
Console.WriteLine($"Sorted: [{string.Join(", ", numbers)}]");

// Reversing array
Array.Reverse(numbers);
Console.WriteLine($"Reversed: [{string.Join(", ", numbers)}]");

// Finding elements
int index = Array.IndexOf(numbers, 8);
Console.WriteLine($"Index of 8: {index}");

// Checking if array contains element
bool contains = Array.Exists(numbers, x => x > 7);
Console.WriteLine($"Contains number > 7: {contains}");
```

## Iterating Through Arrays

Different ways to iterate through arrays:

```csharp
string[] fruits = {"apple", "banana", "cherry", "date"};

// Traditional for loop
Console.WriteLine("Using for loop:");
for (int i = 0; i < fruits.Length; i++)
{
    Console.WriteLine($"  {i}: {fruits[i]}");
}

// Enhanced for-each loop
Console.WriteLine("\nUsing foreach loop:");
foreach (string fruit in fruits)
{
    Console.WriteLine($"  {fruit}");
}

// Using LINQ with index
Console.WriteLine("\nUsing LINQ with index:");
foreach (var (fruit, index) in fruits.Select((value, i) => (value, i)))
{
    Console.WriteLine($"  {index}: {fruit}");
}
```

## Multidimensional Arrays

C# supports multidimensional arrays:

```csharp
// 2D array declaration and initialization
int[,] matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

Console.WriteLine("2D Array:");
for (int i = 0; i < matrix.GetLength(0); i++)
{
    for (int j = 0; j < matrix.GetLength(1); j++)
    {
        Console.Write($"{matrix[i, j]} ");
    }
    Console.WriteLine();
}

// 3D array
int[,,] cube = new int[2, 2, 2];
cube[0, 0, 0] = 1;
cube[1, 1, 1] = 8;

Console.WriteLine($"\n3D array dimensions: {cube.GetLength(0)}x{cube.GetLength(1)}x{cube.GetLength(2)}");
Console.WriteLine($"Element at [0,0,0]: {cube[0, 0, 0]}");
Console.WriteLine($"Element at [1,1,1]: {cube[1, 1, 1]}");
```

## Jagged Arrays

Jagged arrays are arrays of arrays:

```csharp
// Jagged array declaration
int[][] jaggedArray = new int[3][];

// Initialize each sub-array with different sizes
jaggedArray[0] = new int[] {1, 2};
jaggedArray[1] = new int[] {3, 4, 5, 6};
jaggedArray[2] = new int[] {7, 8, 9};

Console.WriteLine("Jagged Array:");
for (int i = 0; i < jaggedArray.Length; i++)
{
    Console.Write($"Row {i}: ");
    for (int j = 0; j < jaggedArray[i].Length; j++)
    {
        Console.Write($"{jaggedArray[i][j]} ");
    }
    Console.WriteLine();
}

// Alternative initialization
string[][] words = {
    new string[] {"hello", "world"},
    new string[] {"C#", "programming", "is", "fun"},
    new string[] {"arrays"}
};

Console.WriteLine("\nString jagged array:");
foreach (var row in words)
{
    Console.WriteLine($"[{string.Join(", ", row)}]");
}
```

## Array Copying

Different methods to copy arrays:

```csharp
int[] original = {1, 2, 3, 4, 5};

// Shallow copy using Clone()
int[] copy1 = (int[])original.Clone();

// Copy using Array.Copy()
int[] copy2 = new int[original.Length];
Array.Copy(original, copy2, original.Length);

// Copy using LINQ
int[] copy3 = original.ToArray();

// Copy portion of array
int[] partial = new int[3];
Array.Copy(original, 1, partial, 0, 3); // Copy 3 elements starting from index 1

Console.WriteLine($"Original: [{string.Join(", ", original)}]");
Console.WriteLine($"Copy1: [{string.Join(", ", copy1)}]");
Console.WriteLine($"Copy2: [{string.Join(", ", copy2)}]");
Console.WriteLine($"Copy3: [{string.Join(", ", copy3)}]");
Console.WriteLine($"Partial: [{string.Join(", ", partial)}]");
```

## Array Searching and Filtering

Using LINQ for advanced array operations:

```csharp
int[] numbers = {1, 5, 8, 12, 15, 20, 25, 30};

// Finding elements
var evenNumbers = numbers.Where(n => n % 2 == 0).ToArray();
Console.WriteLine($"Even numbers: [{string.Join(", ", evenNumbers)}]");

// Finding first element matching condition
var firstLarge = numbers.FirstOrDefault(n => n > 15);
Console.WriteLine($"First number > 15: {firstLarge}");

// Checking conditions
bool allPositive = numbers.All(n => n > 0);
bool anyLarge = numbers.Any(n => n > 50);
Console.WriteLine($"All positive: {allPositive}");
Console.WriteLine($"Any > 50: {anyLarge}");

// Aggregation
int sum = numbers.Sum();
double average = numbers.Average();
int max = numbers.Max();
int min = numbers.Min();

Console.WriteLine($"Sum: {sum}");
Console.WriteLine($"Average: {average:F2}");
Console.WriteLine($"Max: {max}, Min: {min}");
```

## Array Transformation

Transforming arrays with LINQ:

```csharp
string[] words = {"hello", "world", "csharp", "programming"};

// Transform to uppercase
var upperWords = words.Select(w => w.ToUpper()).ToArray();
Console.WriteLine($"Uppercase: [{string.Join(", ", upperWords)}]");

// Transform to word lengths
var lengths = words.Select(w => w.Length).ToArray();
Console.WriteLine($"Lengths: [{string.Join(", ", lengths)}]");

// Transform and filter
var longWords = words.Where(w => w.Length > 5)
                    .Select(w => char.ToUpper(w[0]) + w[1..].ToLower())
                    .ToArray();
Console.WriteLine($"Long words (>5 chars): [{string.Join(", ", longWords)}]");

// Group by length
var groupedByLength = words.GroupBy(w => w.Length)
                          .OrderBy(g => g.Key);

Console.WriteLine("\nGrouped by length:");
foreach (var group in groupedByLength)
{
    Console.WriteLine($"Length {group.Key}: [{string.Join(", ", group)}]");
}
```

## Practical Examples

### Creating and Shuffling an Array

```csharp
// Create array of numbers 1-10
int[] deck = Enumerable.Range(1, 10).ToArray();
Console.WriteLine($"Original deck: [{string.Join(", ", deck)}]");

// Shuffle using Fisher-Yates algorithm
Random random = new Random();
for (int i = deck.Length - 1; i > 0; i--)
{
    int j = random.Next(i + 1);
    (deck[i], deck[j]) = (deck[j], deck[i]);
}

Console.WriteLine($"Shuffled deck: [{string.Join(", ", deck)}]");
```

### Finding Common Elements

```csharp
int[] array1 = {1, 2, 3, 4, 5, 6};
int[] array2 = {4, 5, 6, 7, 8, 9};

// Find intersection
var common = array1.Intersect(array2).ToArray();
Console.WriteLine($"Array1: [{string.Join(", ", array1)}]");
Console.WriteLine($"Array2: [{string.Join(", ", array2)}]");
Console.WriteLine($"Common elements: [{string.Join(", ", common)}]");

// Find union
var union = array1.Union(array2).OrderBy(x => x).ToArray();
Console.WriteLine($"Union: [{string.Join(", ", union)}]");

// Find differences
var onlyInFirst = array1.Except(array2).ToArray();
var onlyInSecond = array2.Except(array1).ToArray();
Console.WriteLine($"Only in first: [{string.Join(", ", onlyInFirst)}]");
Console.WriteLine($"Only in second: [{string.Join(", ", onlyInSecond)}]");
```

## Array Performance Considerations

Arrays in C# are:
- **Fixed size**: Once created, the size cannot be changed
- **Reference types**: Array variables hold references to array objects
- **Zero-based indexing**: First element is at index 0
- **Type safe**: All elements must be of the same type
- **Memory efficient**: Elements are stored in contiguous memory locations

For dynamic sizing, consider using `List<T>` instead of arrays. For better performance with large datasets, consider using `Span<T>` and `Memory<T>` for memory-efficient operations.
