# C# lexical structure

Like human languages, computer languages have a well-defined lexical structure.  
The source code of a C# program is made up of *tokens*, which are the  
smallest meaningful elements in the code. Tokens include identifiers (such as  
variable and method names), keywords (reserved words like `if`,  
`class`, `public`), literals (fixed values such as numbers  
and strings), operators (such as `+`, `-`,  
`=`), delimiters (such as parentheses, braces, commas, and  
semicolons), comments, and white space. The C# compiler reads the source code  
and breaks it down into these tokens to understand and process the program  
correctly.

C# programs are written using characters from the Unicode character set, which  
allows for a wide range of symbols and scripts from many languages around the  
world. This means that C# source code can include not only standard Latin  
letters and digits, but also characters from other alphabets, mathematical  
symbols, and even emoji. Unicode support enables developers to write identifiers  
and string literals in their native languages, making C# a globally accessible  
programming language.

## C# comments

*Comments* are used by humans to clarify the source code. There are three  
types of comments in C#. Single-line comments, multi-line comments and XML  
comments. XML comments can be extracted to HTML files.

Multi-line comments are enclosed by /* */ characters. Single line comments  
start with two forward slashes.

```csharp
/*
    This is Program.cs
    Author: Jan Bodnar
    ZetCode 2022
*/

// A C# statement
Console.WriteLine("This is Comments program");
```

Comments are ignored by C# compiler.

```
/*
  This is Program.cs
/*  Author: Jan Bodnar */
  ZetCode 2022
*/
```

Comments cannot be nested; the above code does not compile.

## C# White Space

White space in C# refers to spaces, tabs, and newlines used in source code. It serves two primary purposes: separating tokens for the compiler and improving code readability for developers.

### Role of White Space

White space is essential in C#, as it separates tokens like keywords, identifiers, and literals. While the compiler ignores extra whitespace in most contexts, it is crucial for readability and maintaining proper code structure.

The following demonstrates how white space affects tokenization:

```
int x = 10;    // Proper spacing between tokens
intx=10;       // Invalid—no space between 'int' and 'x'
int  x  =  10; // Valid—extra spaces are ignored
```

Without proper white space, tokens would merge, making the code impossible to parse. For instance, int x becomes intx, which is not a valid C# statement.

### White Space Rules

C# has strict rules governing white space usage:

- White space is required to separate keywords from identifiers (e.g., `int myVariable`).
- White space cannot appear within identifiers, keywords, or most literals.
- Extra white space between tokens is generally ignored but affects readability.

White space cannot appear inside identifiers, keywords, literals, or operator symbols. For example, you cannot write my variable instead of myvariable for variable names—`int my Variable` is invalid. Extra spaces between tokens are ignored by the compiler. Proper formatting enhances readability, while inconsistent spacing can make code harder to read.

```
int a=1;   // No space around '=' (valid but less readable)
int b = 2; // Proper spacing improves clarity
int c  =  3; // Extra spaces do not affect compilation
```

### Best Practices for White Space

Using consistent indentation and spacing improves readability. Following standard C# coding conventions—such as placing spaces around operators—enhances clarity. Avoid unnecessary white space that does not contribute to better structure.

```
// Poorly formatted code:
if(x==10){Console.WriteLine("Hello");}

// Well-formatted code:
if (x == 10)
{
    Console.WriteLine("Hello");
}
```

Although excess white space is ignored by the compiler, well-structured code improves maintainability and readability, ensuring a more professional and organized codebase.

## C# identifiers

*Identifiers* are tokens that represent names of variables, methods, classes, or other language constructs. In C#, an identifier must start with a letter (a-z, A-Z) or an underscore (_), followed by any combination of letters, digits (0-9), or underscores.

C# identifiers are case-sensitive, meaning `name` and `Name` are considered distinct identifiers. This characteristic allows for more specific naming but requires careful attention to avoid confusion.

### Identifier Rules

Valid identifiers in C# follow these rules:

- Must begin with a letter (a-z, A-Z) or an underscore (_).
- Subsequent characters can be letters, digits (0-9), or underscores.
- Cannot be a C# keyword unless prefixed with @ (e.g., @class).
- Are case-sensitive.

Some examples of valid identifiers:

```
myVariable
_count
firstName
Age
MAX_SIZE
user123
```

Invalid identifiers include:

```
123abc    // Cannot start with a digit
my-name   // Hyphens are not allowed
class     // Reserved keyword (unless @class)
```

VariablesExample.cs

```csharp
public class VariablesExample
{
    public static void Main(string[] args)
    {
        string name = "Robert";
        string Name = "Julia";
        Console.WriteLine(name); // Outputs: Robert
        Console.WriteLine(Name); // Outputs: Julia
    }
}
```

This program demonstrates case sensitivity, as `name` and `Name` are treated as separate variables.

## C# Literals

A *literal* is a direct representation of a specific value within a given type. C# supports various literal types, including boolean, integer, floating point, string, character, and date. Unlike variables, which receive their values at runtime, literals are assigned at compile time.

```
int age = 29;
string nationality = "Hungarian";
```

In the example above, `29` is an integer literal, while `"Hungarian"` is a string literal.

```csharp
bool isSingle = true;
string name = "James";
string job = null;
double weight = 68.5;
DateTime birthDate = DateTime.Parse("November 12, 1987");

Console.WriteLine($"His name is {name}");

if (isSingle)
{
    Console.WriteLine("He is single");
}
else
{
    Console.WriteLine("He is in a relationship");
}

Console.WriteLine($"His job is {job}");
Console.WriteLine($"He weighs {weight} kilograms");
Console.WriteLine($"He was born in {birthDate:yyyy}");
```

The example above demonstrates different literal types:

- A `bool` literal can hold either `true` or `false`.
- The value `"James"` is a string literal.
- The keyword `null` represents an unassigned value.
- `68.5` is a floating-point literal.
- The date `November 12, 1987` is a date literal.

```
$ dotnet run
His name is James
He is single
His job is 
He weighs 68.5 kilograms
He was born in 1987
```

## C# operators

An *operator* is a symbol used to perform an action on some value. Operators are used in  
expressions to describe operations involving one or more operands.

```
+    -    *    /    %    ^    &    |    !    ~
=    +=   -=   *=   /=   %=    ^=    ++    --
==   !=    <   >    &=  >>=   <<=   >=   <=
||   &&    >>    <<    ?:
```

The above example shows various C# operators.

```csharp
int a = 10;
int b = 11;
int c = 12;

a = a + b + c;
Console.WriteLine(c);
```

We use the addition and assignment operators in this code example.

```
$ dotnet run
33
```

## C# delimiters

*Delimiters* are characters used to separate or group elements in C# code. They help define the structure and organization of statements, expressions, and code blocks. Common delimiters in C# include parentheses, braces, brackets, semicolons, and commas.

```csharp
int[] numbers = {1, 2, 3, 4, 5};

for (int i = 0; i < numbers.Length; i++)
{
    Console.WriteLine(numbers[i]);
}
```

In this example:

- `{}` are used to define the array and the code block.
- `()` are used for method parameters and control structures.
- `[]` are used for array indexing.
- `;` terminates statements.
- `,` separates array elements.

```
int a, b, c;
```

The comma character can be used to use multiple declarations on the same line of code.

## C# Keywords

Keywords in C# are reserved words that have special meaning within the language. They are used to define variables, control program flow, and perform logical operations, ensuring a structured and functional codebase.

C# includes a wide range of keywords, such as `if`, `else`, `for`, `while`, `base`, `false`, `float`, `catch`, and `this`. These keywords play a crucial role in various aspects of programming and are introduced progressively throughout the tutorial.


```csharp
for (int i = 0; i <= 5; i++)
{
    Console.WriteLine(i);
}
```

In the example above, the `int` keyword defines a variable type, while the `for` keyword initiates a loop, demonstrating fundamental control flow and data handling in C#.

## C# Unicode Support

C# uses the Unicode character set, allowing identifiers, literals, and comments to include characters from various languages, such as Cyrillic, Chinese, or Arabic. This makes C# suitable for internationalization.

UnicodeExample.cs

```csharp
public class UnicodeExample
{
    public static void Main(string[] args)
    {
        string имя = "Анна"; // Russian identifier and string
        Console.WriteLine($"Имя: {имя}");
        string 名前 = "太郎"; // Japanese identifier and string
        Console.WriteLine($"名前: {名前}");
    }
}
```

This example uses Unicode identifiers and literals in Russian and Japanese, demonstrating C#'s support for global character sets.

## C# Preprocessor Directives

Preprocessor directives are special instructions that are processed before compilation. They allow conditional compilation, symbol definition, and other compile-time behaviors. All preprocessor directives begin with `#`.

These directives do not produce executable code but influence how the compiler handles source code. Common preprocessor directives include `#define`, `#if`, `#else`, `#elif`, `#endif`, `#region`, and `#pragma`.

PreprocessorExample.cs

```csharp
#define DEBUG

public class PreprocessorExample
{
    public static void Main(string[] args)
    {
        #if DEBUG
            Console.WriteLine("Debug mode is active");
        #else
            Console.WriteLine("Release mode is active");
        #endif
    }
}
```

This example shows conditional compilation using preprocessor directives:

- `#define DEBUG` defines the symbol `DEBUG`.
- `#if DEBUG` checks if the symbol `DEBUG` is defined.
- `#else` specifies an alternative code path if the symbol is not defined.
- `#endif` marks the end of the conditional directive.

Preprocessor directives are useful for managing debug and release configurations, organizing code blocks, and enhancing compiler behavior without altering runtime execution.

## C# Line Terminators

Line terminators mark the end of a line in the source code. In C#, valid line terminators include the carriage return (`\r`), line feed (`\n`), or the combination (`\r\n`). They affect how the compiler parses tokens.

Unlike some languages, C# does not require a semicolon to terminate every line, but statements must be separated by semicolons. Line terminators help the compiler identify token boundaries.

LineTerminatorExample.cs

```csharp
public class LineTerminatorExample
{
    public static void Main(string[] args)
    {
        Console.WriteLine("Line 1");
        Console.WriteLine("Line 2");
    }
}
```

Each statement ends with a semicolon and is separated by a line terminator, ensuring proper parsing by the compiler.

## C# conventions

Conventions are recommended practices for writing consistent and readable C# code. While not enforced by the compiler, they improve code maintainability and collaboration. Below are key C# conventions:

- *PascalCase for identifiers*: Classes, methods, and properties start with an uppercase letter (e.g., `MyClass`, `GetName`).
- *camelCase for variables*: Local variables and parameters start with a lowercase letter (e.g., `myVariable`, `itemCount`).
- *Meaningful names*: Use descriptive names that indicate the purpose (e.g., `CalculateTotal` instead of `calc`).
- *Constants in UPPERCASE*: Use all caps with underscores for constants (e.g., `MAX_SIZE`, `DEFAULT_TIMEOUT`).

Following these conventions makes C# code more readable and professional, facilitating better collaboration and code maintenance.
