
<!DOCTYPE html>
<html lang="en">
<head>
<title>C# lexical structure - C# grammar</title>
<link rel="stylesheet" href="/cfg/style.css" type="text/css">
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="keywords" content="C#, lexical structure, syntax rules, programming
fundamentals, .NET language, C# tokens, code structure">
<meta name="description" content="Discover the lexical structure of C#,
including syntax rules, tokens, and fundamental building blocks of the language.
Like human languages, programming languages have a defined structure—learn how
C# handles lexical elements.">

<meta name="author" content="Jan Bodnar">

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-9706709751191532"
     crossorigin="anonymous"></script>
</head>

<body>

<header>

<div>
<a href="/" title="Home">ZetCode</a>
</div>

<nav>
    <a title="All tutorials" href="/all/">All</a>
    <a title="Go tutorials" href="/golang/">Golang</a>
    <a title="Python tutorials" href="/python/">Python</a>
    <a title="C# tutorials" href="/csharp/">C#</a>
    <a title="Java tutorials" href="/java/">Java</a>
    <a title="JavaScript tutorials" href="/javascript/">JavaScript</a>
    <a title="Subscribe to ZetCode news" href="http://zetcode.us13.list-manage.com/subscribe?u=9def9ccd4c70dbbaf691f90fc&id=6556210f80">Subscribe</a>
</nav>

</header>

<div class="container">

<div class="ltow">

<div id="ebooks">

<h2 class="blu">Ebooks</h2>

<ul>
<li><a href="/ebooks/advancedpyqt5/">PyQt5 ebook</a></li>
<li><a href="/ebooks/tkinter/">Tkinter ebook</a></li>
<li><a href="/ebooks/sqlitepython/">SQLite Python</a></li>
<li><a href="/ebooks/advancedwxpython/">wxPython ebook</a></li>
<li><a href="/ebooks/windowsapi/">Windows API ebook</a></li>
<li><a href="/ebooks/advancedjavaswing/">Java Swing ebook</a></li>
<li><a href="/ebooks/javagames/">Java games ebook</a></li>
<li><a href="/ebooks/mysqljava/">MySQL Java ebook</a></li>
</ul>

</div>

</div>


<div class="content">

<h1>C# lexical structure</h1>

<p class="last_mod">
last modified May 16, 2025
</p>
 
<p>
Like human languages, computer languages have a well-defined lexical structure.
The source code of a C# program is made up of <em>tokens</em>, which are the
smallest meaningful elements in the code. Tokens include identifiers (such as
variable and method names), keywords (reserved words like <code>if</code>,
<code>class</code>, <code>public</code>), literals (fixed values such as numbers
and strings), operators (such as <code>+</code>, <code>-</code>,
<code>=</code>), delimiters (such as parentheses, braces, commas, and
semicolons), comments, and white space. The C# compiler reads the source code
and breaks it down into these tokens to understand and process the program
correctly.
</p>

<p>
C# programs are written using characters from the Unicode character set, which
allows for a wide range of symbols and scripts from many languages around the
world. This means that C# source code can include not only standard Latin
letters and digits, but also characters from other alphabets, mathematical
symbols, and even emoji. Unicode support enables developers to write identifiers
and string literals in their native languages, making C# a globally accessible
programming language.
</p>


<h2>C# comments</h2>

<p>
<em>Comments</em> are used by humans to clarify the source code. There are three
types of comments in C#. Single-line comments, multi-line comments and XML
comments. XML comments can be extracted to HTML files.
</p>

<p>
Multi-line comments are enclosed by /* */ characters. Single line comments
start with two forward slashes.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
/*
    This is Program.cs
    Author: Jan Bodnar
    ZetCode 2022
*/

// A C# statement
Console.WriteLine("This is Comments program");
</pre>

<p>
Comments are ignored by C# compiler.
</p>

<pre class="compact">
/*
  This is Program.cs
/*  Author: Jan Bodnar */
  ZetCode 2022
*/
</pre>

<p>
Comments cannot be nested; the above code does not compile.
</p>


<h2>C# White Space</h2>

<p>
White space in C# refers to spaces, tabs, and newlines used in source code. It serves two primary purposes: separating tokens for the compiler and improving code readability for developers.
</p>

<h3>Role of White Space</h3>

<p>
White space is required in certain places to distinguish keywords, identifiers,
and symbols. It also improves code clarity, making it easier to read and
maintain. While necessary in some cases, excessive white space does not affect
compilation.
</p>

<pre class="compact">
int i = 0;
string message = "Hello, World!";
</pre>

<p>
In this example, white space separates the <code>int</code> keyword from the
variable name <code>i</code>, ensuring the compiler correctly interprets each
token.
</p>

<h3>Rules for White Space in C#</h3>

<p>
White space must be placed between a type declaration and its identifier, such
as <code>int value</code>. However, it cannot be used within keywords or
variable names—<code>int my Variable</code> is invalid. Extra spaces between
tokens are ignored by the compiler. Proper formatting enhances readability,
while inconsistent spacing can make code harder to read.
</p>

<pre class="compact">
int a=1;   // No space around '=' (valid but less readable)
int b = 2; // Proper spacing improves clarity
int c  =  3; // Extra spaces do not affect compilation
</pre>

<h3>Best Practices for White Space</h3>

<p>
Using consistent indentation and spacing improves readability. Following
standard C# coding conventions—such as placing spaces around operators—enhances
clarity. Avoid unnecessary white space that does not contribute to better
structure.
</p>

<pre class="compact">
// Poorly formatted code:
if(x==10){Console.WriteLine("Hello");}

// Well-formatted code:
if (x == 10)
{
    Console.WriteLine("Hello");
}
</pre>

<p>
Although excess white space is ignored by the compiler, well-structured code
improves maintainability and readability, ensuring a more professional and
organized approach to C# development.
</p>

<h2>C# Variables</h2>

<p>
A variable is an identifier that references a memory location holding a value.
Variables are assigned values during program execution. Identifiers can include
letters, digits, and underscores, but must start with a letter or underscore,
not a digit.
</p>

<p>
C# is case-sensitive, so <code>Name</code>, <code>name</code>, and
<code>NAME</code> are distinct variables. Keywords cannot be used as identifiers
unless prefixed with <code>@</code> (e.g., <code>@int</code>), but this is
discouraged.
</p>

<pre class="compact">
string userName;
int _count;
DateTime birthDate;
</pre>

<p>
These are valid identifiers. 
</p>

<pre class="compact">
string 123name; // Starts with a digit
int %count;     // Contains invalid character
DateTime birth date; // Contains space
</pre>

<p>
These are invalid identifiers.
</p>

<div class="codehead">VariablesExample.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
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
</pre>

<p>
This program demonstrates case sensitivity, as <code>name</code> and
<code>Name</code> are treated as separate variables.
</p>





<h2>C# Literals</h2>

<p>
A <em>literal</em> is a direct representation of a specific value within a given
type. C# supports various literal types, including boolean, integer, floating
point, string, character, and date. Unlike variables, which receive their values
at runtime, literals are assigned at compile time.
</p>

<pre class="compact">
int age = 29;
string nationality = "Hungarian";
</pre>

<p>
In the example above, <code>29</code> is an integer literal, while
<code>"Hungarian"</code> is a string literal.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
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
</pre>

<p>
The example above demonstrates different literal types:
</p>

<ul>
    <li>A <code>bool</code> literal can hold either <code>true</code> or <code>false</code>.</li>
    <li>The value <code>"James"</code> is a string literal.</li>
    <li>The keyword <code>null</code> represents an unassigned value.</li>
    <li><code>68.5</code> is a floating-point literal.</li>
    <li>The date <code>November 12, 1987</code> is a date literal.</li>
</ul>

<pre class="compact">
$ dotnet run
His name is James
He is single
His job is
He weighs 68.5 kilograms
He was born in 1987
</pre>

<h2>C# operators</h2>

<p>
An <em>operator</em> is a symbol used to perform an action on some value.
Operators are used in expressions to describe operations involving one or more
operands.
</p>

<pre class="compact">
+    -    *    /    %    ^    &amp;    |    !    ~
=    +=   -=   *=   /=   %=    ^=    ++    --
==   !=    &lt;   &gt;    &amp;=  &gt;&gt;=   &lt;&lt;=   &gt;=   &lt;=
||   &amp;&amp;    &gt;&gt;    &lt;&lt;    ?:
</pre>

<p>
This is a partial list of C# operators. We will talk about operators later in
the tutorial.
</p>


<h2>C# separators</h2>

<p>
A <em>separator</em> is a sequence of one or more characters used
to specify the boundary between separate, independent regions in plain text or
other data stream.
</p>

<pre class="compact">
[ ]   ( )   { }   ,   :   ;
</pre>

<pre class="compact">
string language = "C#";
</pre>

<p>
The double characters are used to mark the beginning and the end of a string.
The semicolon (;) character is used to end each C# statement.
</p>

<pre class="compact">
Console.WriteLine("Today is {0}", DateTime.Today.ToString("M/d"));
</pre>

<p>
Parentheses (round brackets) are used to mark the method signature. The
signature consists of method parameters. Curly brackets are used to denote
the evaluated value.
</p>

<pre class="compact">
int[] array = new int[5] {1, 2, 3, 4, 5};
</pre>

<p>
Square brackets <code>[]</code> are used to denote an array type. They are also
used to access or modify array elements. Curly brackets <code>{}</code> are also
used to initiate arrays. Curly brackets are also used in variable
interpolation or to enclose the body of a method or a class.
</p>

<pre class="compact">
int a, b, c;
</pre>

<p>
The comma character can be used to use multiple declarations on the
same line of code.
</p>


<h2>C# Keywords</h2>

<p>
Keywords in C# are reserved words that have special meaning within the language.
They are used to define variables, control program flow, and perform logical
operations, ensuring a structured and functional codebase.
</p>

<p>
C# includes a wide range of keywords, such as <code>if</code>,
<code>else</code>, <code>for</code>, <code>while</code>, <code>base</code>,
<code>false</code>, <code>float</code>, <code>catch</code>, and
<code>this</code>. These keywords play a crucial role in various aspects of
programming and are introduced progressively throughout the tutorial.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
for (int i = 0; i &lt;= 5; i++)
{
    Console.WriteLine(i);
}
</pre>

<p>
In the example above, the <code>int</code> keyword defines a variable type,
while the <code>for</code> keyword initiates a loop, demonstrating fundamental
control flow and data handling in C#.
</p>

<h2>C# Unicode Support</h2>

<p>
C# uses the Unicode character set, allowing identifiers, literals, and comments
to include characters from various languages, such as Cyrillic, Chinese, or
Arabic. This makes C# suitable for internationalization.
</p>

<div class="codehead">UnicodeExample.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
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
</pre>

<p>
This example uses Unicode identifiers and literals in Russian and Japanese,
demonstrating C#'s support for global character sets.
</p>


<h2>C# Preprocessor Directives</h2>

<p>
Preprocessor directives are special instructions that are processed before
compilation. They allow conditional compilation, symbol definition, and other
compile-time behaviors. All preprocessor directives begin with <code>#</code>.
</p>

<p>
These directives do not produce executable code but influence how the compiler
handles source code. Common preprocessor directives include
<code>#define</code>, <code>#if</code>, <code>#else</code>, <code>#elif</code>,
<code>#endif</code>, <code>#region</code>, and <code>#pragma</code>.
</p>

<div class="codehead">PreprocessorExample.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
#define DEBUG

public class PreprocessorExample
{
    public static void Main(string[] args)
    {
        #if DEBUG
            Console.WriteLine("Debug mode is active");
        #else
            Console.WriteLine("Debug mode is inactive");
        #endif
    }
}
</pre>

<p>
In the example above:
</p>

<ul>
    <li><code>#define DEBUG</code> declares a preprocessor symbol.</li>
    <li><code>#if DEBUG</code> checks if the symbol <code>DEBUG</code> is defined.</li>
    <li><code>#else</code> specifies an alternative code path if the symbol is not defined.</li>
    <li><code>#endif</code> marks the end of the conditional directive.</li>
</ul>

<p>
Preprocessor directives are useful for managing debug and release
configurations, organizing code blocks, and enhancing compiler behavior without
altering runtime execution.
</p>


<h2>C# Line Terminators</h2>

<p>
Line terminators mark the end of a line in the source code. In C#, valid line
terminators include the carriage return (<code>\r</code>), line feed
(<code>\n</code>), or the combination (<code>\r\n</code>). They affect how the
compiler parses tokens.
</p>

<p>
Unlike some languages, C# does not require a semicolon to terminate every line,
but statements must be separated by semicolons. Line terminators help the
compiler identify token boundaries.
</p>

<div class="codehead">LineTerminatorExample.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
public class LineTerminatorExample
{
    public static void Main(string[] args)
    {
        Console.WriteLine("Line 1");
        Console.WriteLine("Line 2");
    }
}
</pre>

<p>
Each statement ends with a semicolon and is separated by a line terminator,
ensuring proper parsing by the compiler.
</p>


<h2>C# conventions</h2>

<p>
Conventions are recommended practices for writing consistent and readable C#
code. While not enforced by the compiler, they improve code maintainability and
collaboration. Below are key C# conventions:
</p>

<ul>
<li><em>PascalCase for identifiers</em>: Classes, methods, and properties start with an uppercase letter (e.g., <code>MyClass</code>, <code>GetName</code>).</li>
<li><em>Interface names</em>: Start with <code>I</code> (e.g., <code>IEnumerable</code>).</li>
<li><em>Comments</em>: Place on separate lines, not at the end of code lines, for clarity.</li>
<li><em>One statement per line</em>: Avoid multiple statements on a single line.</li>
<li><em>Meaningful names</em>: Use descriptive identifiers like <code>customerName</code> instead of <code>cn</code>.</li>
<li><em>Constants</em>: Use uppercase with underscores (e.g., <code>MAX_COUNT</code>).</li>
<li><em>Curly braces</em>: Place opening braces on a new line for code blocks.</li>
<li><em>Main method parameter</em>: Name the string array parameter <code>args</code>.</li>
<li><em>Keyword order</em>: Place <code>public</code> before <code>static</code> in declarations.</li>
<li><em>Indentation</em>: Use consistent 4-space indentation for nested code.</li>
<li><em>File naming</em>: Match the file name to the main class name (e.g., <code>Program.cs</code> for <code>Program</code> class).</li>
</ul>

<p>
This article explored the lexical structure of C#, including tokens like
comments, variables, literals, operators, separators, and keywords. Additional
topics like Unicode support, preprocessor directives, and line terminators were
covered to provide a comprehensive understanding. Adhering to C# conventions
ensures high-quality, maintainable code.
</p>

<h2>Source</h2>

<p>
<a href="https://learn.microsoft.com/en-us/dotnet/csharp/">C# documentation</a>
</p>

<h2 id="author">Author</h2>

<p class="author">
My name is Jan Bodnar, and I am a passionate programmer with extensive
programming experience. I have been writing programming articles since 2007.
To date, I have authored over 1,400 articles and 8 e-books. I possess more
than ten years of experience in teaching programming.
</p>

<p>
List <a href="/csharp/">all C# tutorials</a>.
</p>


</div> <!-- content -->

</div> <!-- container -->

<footer>

<nav>
<a title="Home page" href="/">Home</a>
<a title="Follow on Twitter" href="https://twitter.com/janbodnar">Twitter</a>
<a title="Visit Github" href="https://github.com/janbodnar">Github</a>
<a title="Subscribe to ZetCode news" href="http://zetcode.us13.list-manage.com/subscribe?u=9def9ccd4c70dbbaf691f90fc&id=6556210f80">Subscribe</a>
<a title="Privacy policy" href="/privacy">Privacy</a>
<a title="About" href="/about/">About</a>
</nav>

<div>
<span>&copy; 2007 - 2025 Jan Bodnar</span>
<span>admin(at)zetcode.com</span>
</div>

</footer>

<script src="/cfg/utils.js"></script>
</body>
</html>

