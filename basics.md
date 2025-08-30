
<!DOCTYPE html>
<html lang="en">
<head>
<title>C# basics - covering basics of C#</title>
<link rel="stylesheet" href="/cfg/style.css" type="text/css">
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="keywords" content="C#, basics, tutorial, programming language, .NET, learn C#">
<meta name="description" content="C# basics tutorial covers the basics of C#
programming. We work with variables, constants and basic data types. We read and
write to the console; we mention variable interpolation.">

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


<h1>C# basics</h1>

<p class="last_mod">
last modified January 17, 2024
</p>
 
<p>
In this article we cover basic programming concepts of the C# language. We
introduce the very basic programs. We work with variables, constants and basic
data types. We read and write to the console; we mention variable interpolation.
</p>


<h2>C# old school example</h2>

<p>
We start with a traditional C# example.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
using System;

namespace Simple
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("This is C#");
        }
    }
}
</pre>

<p>
The program prints "This is C#" message to the console. We explain it line by
line.
</p>

<pre class="explanation">
using System;
</pre>

<p>
The <code>using</code> keyword imports a specific namespace to our program.
Namespaces are created to group and/or distinguish named entities from other
ones. This prevents name conflicts. This line is a C# statement. Each statement
is ended with a semicolon.
</p>

<pre class="explanation">
namespace Simple
{
</pre>

<p>
We declare a namespace. Namespaces are used to organize code and to prevent
name clashes.
</p>

<pre class="explanation">
class Program
{
    ...
}
</pre>

<p>
Each C# program is structured. It consists of classes and its members. A class
is a basic building block of a C# program. The above code is a class definition.
The definition has a body, which starts with a left curly brace <code>{</code>
and ends with a right curly brace <code>}</code>.
</p>

<pre class="explanation">
static void Main(string[] args)
{
    ...
}
</pre>

<p>
The <code>Main</code> is a method. A method is a piece of code created to do a
specific job. Instead of putting all code into one place, we divide it into
pieces, called methods. This brings modularity to our application. Each method
has a body, in which we place statements. The body of a method is enclosed by
curly brackets.
</p>

<p>
The specific job for the <code>Main</code> method is to start the application.
It is the entry point to each console C# program. The method is declared to be
<code>static</code>. This static method can be called without the need
to create an instance of the <code>Program</code> class. First we need start the
application and after that, we are able to create instances of classes. The 
<code>void</code> keyword signifies that the method does not return any value. 
(Methods may or may not return values.)
</p>

<p>
The <code>Main</code> method has the <code>args</code> argument, which stores
command line arguments. Through command line arguments, users of the program can 
pass it values.
</p>

<pre class="explanation">
Console.WriteLine("This is C#");
</pre>

<p>
In this code line, we print the "This is C#" string to the console. To print a
message to the console, we use the <code>WriteLine</code> method of the
<code>Console</code> class. The class represents the standard input, output, and
error streams for console applications. Note that <code>Console</code> class is
part of the <code>System</code> namespace. This line was the reason to import
the namespace with the <code>using System;</code>
statement. If we didn't use the statement, we would have to use the fully
qualified name of the <code>WriteLine</code> method:
<code>System.Console.WriteLine("This is C#");</code>.
</p>

<pre class="compact">
$ dotnet run
This is C#
</pre>


<h2>C# basic example simplified</h2>

<p>
Over the years, C# has been significantly improved and simplified. The language 
became much more approachable for beginners.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
namespace Simple;

class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine("This is C#");
    }
}
</pre>

<p>
Since C# 10, we can omit the <code>using System;</code> statement. It is
automatically included with <em>implicit usings</em>. 
</p>

<pre class="explanation">
namespace Simple;
</pre>

<p>
Also, the namespace declaration can be reduced as well (C# 10). This is called 
file-scoped namespace and it reduces the need for a block and indentation.
</p>

<hr>

<p>
With top-level statements (C# 9), we can further simplify the code.  
We don't need to use the <code>Main</code> method as a starting point and the
code does not have to be placed inside an application class.
</p>

<div class="note">
<strong>Note: </strong> Only one file in the application may use top-level
statements.
</div>

<p>
For small programs, we can also omit the namespace declaration.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
Console.WriteLine("This is C#");
</pre>

<p>
Now the original 12 line code example was reduced to a single line of code.
</p>



<h2>C# console reading values</h2>

<p>
We can use the <code>Console</code> class to read values as well.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
Console.Write("Enter your name: ");

string name = Console.ReadLine();
Console.WriteLine($"Hello {name}");
</pre>

<p>
The second program reads a value from a console and prints it.
</p>

<pre class="explanation">
string name = Console.ReadLine();
</pre>

<p>
We read a line from the terminal. When we hit the Enter key, the input is
assigned to the name variable. The input is stored into the
<code>name</code> variable, which is declared to be of type <code>string</code>.
</p>

<pre class="explanation">
Console.WriteLine($"Hello {name}");
</pre>

<p>
In this code line, we do string formatting. The <code>{name}</code> specifier
is replaced with the value of the <code>name</code> variable.
</p>

<pre class="compact">
$ dotnet run
Enter your name: Jan
Hello Jan
</pre>


<h2>C# command line arguments</h2>

<p>
C# programs can receive command line arguments. They follow the name of the
program, when we run it. A C# program receives command line arguments in the
<code>args</code> array of strings.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
for (int i = 0; i &lt; args.Length; i++)
{
    Console.WriteLine($"{args[i]}");
}
</pre>

<p>
Command line arguments can be passed to the <code>Main</code>method.
</p>

<pre class="explanation">
for (int i = 0; i &lt; args.Length; i++)
{
    Console.WriteLine($"{args[i]}");
}
</pre>

<p>
We go through the array of these arguments with a for loop and print them to the
console. The <code>Length</code> property gives the number of elements in the
array. Loops and arrays will be described in more detail later.
</p>

<pre class="compact">
$ dotnet run 1 2 3
1
2
3
</pre>

<p>
We provide three numbers as command line arguments and these are printed to the
console.
</p>


<h2>C# variables</h2>

<p>
A <em>variable</em> is a place to store data. A variable has a name and a data
type. A data type determines what values can be assigned to the variable, for
instance integers, strings, or boolean values. Over the time of the program
variables can obtain various values of the same data type. Variables are always
initialized to the default value of their type before any reference to the
variable can be made.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
string city = "New York";
string name = "Paul"; int age = 35;
string nationality = "American";

Console.WriteLine(city);
Console.WriteLine(name);
Console.WriteLine(age);
Console.WriteLine(nationality);

city = "London";
Console.WriteLine(city);
</pre>

<p>
In the example we have four variables.
</p>

<pre class="explanation">
string city = "New York";
</pre>

<p>
We declare a city variable of the string type and
initialize it to the "New York" value.
</p>

<pre class="explanation">
string name = "Paul"; int age = 35;
</pre>

<p>
We declare and initialize two more variables. We can put two statements on one
line. But for readability reasons, each statement should be on a separate line.
</p>

<pre class="explanation">
Console.WriteLine(city);
Console.WriteLine(name);
Console.WriteLine(age);
Console.WriteLine(nationality);
</pre>

<p>
We print the values of the variables to the terminal.
</p>

<pre class="explanation">
city = "London";
</pre>

<p>
We assign a new value to the <code>city</code> variable.
</p>

<pre class="compact">
$ dotnet run
New York
Paul
35
American
London
</pre>


<h2>The var keyword</h2>

<p>
Variables at a method scope can be implicitly typed using the <code>var</code>
keyword. The variables are always strongly typed, but with <code>var</code>
the type is inferred by C# compiler from the right side of the assignment.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
var name = "Peter";
var age = 23;

Console.WriteLine($"{name} is {age} years old");

name = "Jozef";
age = 32;

Console.WriteLine($"{name} is {age} years old");

Console.WriteLine(name.GetType());
Console.WriteLine(age.GetType());
</pre>

<p>
In the program we have two implicitly typed variables.
</p>

<pre class="explanation">
var name = "Peter";
var age = 23;
</pre>

<p>
On the left side of the assignment we use the <code>var</code> keyword.
The <code>name</code> variable is of <code>string</code> type and the
<code>age</code> of <code>int</code>. The types are inferred from the right side
of the assignment.
</p>

<pre class="explanation">
Console.WriteLine(name.GetType());
Console.WriteLine(age.GetType());
</pre>

<p>
We determine the types of the variables with <code>GetType</code>.
</p>

<pre class="compact">
$ dotnet run
Peter is 23 years old
Jozef is 32 years old
System.String
System.Int32
</pre>


<h2>C# List collection</h2>

<p>
While variables hold single values, multiple values can be added to collections.
A <code>List</code> is a sequence of elements, which can be accessed by indexing
operation with <code>[]</code>. Elements of a list can be traversed with e.g. a
<code>foreach</code> keyword.
</p>

<p>
The <code>List</code> type is resides in the 
<code>System.Collections.Generic</code>, which is included with implicit usings.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
List&lt;string&gt; words = ["stone", "rock", "falcon", "sky"];

Console.WriteLine(words[2]);

Console.WriteLine();

foreach (var word in words)
{
    Console.WriteLine(word);
}
</pre>

<p>
In the example, we work a list of words.
</p>

<pre class="explanation">
List&lt;string&gt; words = ["stone", "rock", "falcon", "sky"];
</pre>

<p>
A list object is created. Between the angle brackets (<code>&lt;&gt;</code>) we
specify the data type of the list elements. The list is initialized with
elements inside the square brackets (<code>[]</code>). Each element of the list 
is separated with comma.
</p>

<pre class="explanation">
Console.WriteLine(words[2]);
</pre>

<p>
Here we print the third element to the console. (The indexes start from 0.)
</p>

<pre class="explanation">
foreach (var word in words)
{
    Console.WriteLine(word);
}
</pre>

<p>
Using a foreach loop, we go through all elements of the list and print them to
the console. In each of the cycles, the
<code>word</code> variable is given one of the elements from the list.
</p>

<pre class="compact">
$ dotnet run
falcon

stone
rock
falcon
sky
</pre>


<h2>C# discards</h2>

<p>
<em>Discards</em> are special, write-only variables which are used to trash the
values that are not interesting to the programmer. The <code>_</code>
(underscore character) is used for a discard.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
var vals = (1, 2, 3, 4, 5, 6);

(int x, int y, int z, _, _, _) = vals;

Console.WriteLine(x);
Console.WriteLine(y);
Console.WriteLine(z);
</pre>

<p>
The example defines a tuple of values. By using a deconstruction operation, we
assign the values of the tuples into variables.
</p>

<pre class="explanation">
var vals = (1, 2, 3, 4, 5, 6);
</pre>

<p>
We define a tuple of six values. A tuple is a collection of ordered,
heterogeneous elements.
</p>

<pre class="explanation">
(int x, int y, int z, _, _, _) = vals;
</pre>

<p>
Say, we are interested only in the first three values of the tuple. On the left
side of the assignment, we define three variables: <code>x</code>,
<code>y</code>, and <code>y</code>. Since the <code>vals</code> tuple has six
elements, we need to have six variables on the left side as well. Here we can
use the <code>_</code> character for the remainding variables. This way we
indicate that currently these values are not important to us an we won't work
with them.
</p>


<h2>C# Range method</h2>

<p>
The <code>Range</code> method generates a sequence of numbers within a specified
range. The first parameter is the value of the first integer in the sequence.
The second parameter is the  number of sequential integers to generate.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
foreach(var el in Enumerable.Range(1, 10))
{
    Console.WriteLine(el);
}
</pre>

<p>
The example prints values 1..10 to the terminal using a foreach loop. The
sequence of the integers were generated with the <code>Range</code>
method.
</p>


<h2>C# constants</h2>

<p>
Unlike variables, <em>constants</em> retain their values. Once initialized, they
cannot be modified. Constants are created with the <code>const</code> keyword.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
const int WIDTH = 100;
const int HEIGHT = 150;
int var = 40;

var = 50;

// WIDTH = 110;
</pre>

<p>
In this example, we declare two constants and one variable.
</p>

<pre class="explanation">
const int WIDTH = 100;
const int HEIGHT= 150;
</pre>

<p>
We use the <code>const</code> keyword to inform the compiler that we declare a
constant. It is a convention to write constants in upper case letters.
</p>

<pre class="explanation">
int var = 40;

var = 50;
</pre>

<p>
We declare and initialize a variable. Later, we assign a new value to the
variable.
</p>

<pre class="explanation">
// WIDTH = 110;
</pre>

<p>
This is not possible with a constant. If we uncomment this line, we get a
compilation error.
</p>


<h2>C# string formatting</h2>

<p>
Building strings from variables is a very common task in programming.
C# has the <code>string.Format</code> method to format strings.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
int age = 34;
string name = "William";

string msg = string.Format("{0} is {1} years old.", name, age);
Console.WriteLine(msg);
</pre>

<p>
Strings are immutable in C#. We cannot modify an existing string. We must create
a new string from existing strings and other types. In the code example, we
create a new string. We also use values from two variables.
</p>

<pre class="explanation">
int age = 34;
string name = "William";
</pre>

<p>
Here we define two variables.
</p>

<pre class="explanation">
string msg = string.Format("{0} is {1} years old.", name, age);
</pre>

<p>
We use the <code>Format</code> method of the built-in string class. The
<code>{0}</code>, <code>{1}</code> are the places where the variables are
evaluated. The numbers represent the position of the variable. The
<code>{0}</code> evaluates to the first supplied variable and the
<code>{1}</code> to the second.
</p>

<pre class="compact">
$ dotnet run
William is 34 years old.
</pre>


<h2>C# string interpolation</h2>

<p>
Some dynamic languages like Perl, PHP or Ruby support string/variable
interpolation. Variable interpolation is replacing variables with their values
inside string literals. C# supports variable interpolation since C# 6.0.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
string name = "Peter";
int age = 34;

string msg = $"{name} is {age} years old";

Console.WriteLine(msg);
</pre>

<p>
In the code example, we build a string using variable interpolation.
</p>

<pre class="explanation">
string msg = $"{name} is {age} years old";
</pre>

<p>
The string is preceded with the <code>$</code> character and the variables
are inside curly brackets.
</p>

<pre class="compact">
$ dotnet run
Peter is 34 years old
</pre>

<h2>Source</h2>

<p>
<a href="https://learn.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/">A tour of the C# language</a>
</p>

<p>
In this article we covered some basics of the C# language.
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

