
<!DOCTYPE html>
<html lang="en">
<head>
<title>C# string - working with strings in C# language</title>
<link rel="stylesheet" href="/cfg/style.css" type="text/css">
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="keywords" content="C#, learn C#, C# tutorial, string data type in
C#, C# strings, Unicode characters in C#, C# programming, .NET, learn .NET, .NET
framework">
<meta name="description" content="Discover how to work with strings in C#
through this comprehensive tutorial. Learn about the string data type, Unicode
characters, and the fundamentals of C# programming within the .NET framework.">

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

<h1>C# string</h1>

<p class="last_mod">
last modified May 1, 2025
</p>
 
<p>
In this article we show how to work with strings in C#. 
</p>


<h2>Understanding C# Strings</h2>

<p>
A string in C# represents a sequence of characters encoded using UTF-16. It is a
fundamental data type that stores a series of characters according to a specific
character encoding. When a string appears directly in source code, it is
referred to as a <em>string literal</em>.
</p>

<p>
In C#, strings are objects, and there are two primary classes available for
handling them:
</p>

<ul>
  <li><code>System.String</code></li>
  <li><code>System.Text.StringBuilder</code></li>
</ul>

<p>
The <code>System.String</code> class provides immutable strings, meaning that
once created, their content cannot be altered. On the other hand, the
<code>System.Text.StringBuilder</code> class is designed for mutable strings,
enabling efficient modifications like appending or replacing characters.
</p>

<p>
In C#, the <code>string</code> keyword is an alias for
<code>System.String</code>. While <code>string</code> is specific to the C#
language, <code>System.String</code> belongs to the .NET framework, and the two
can be used interchangeably.
</p>

<div class="note">
<strong>Note:</strong> This article focuses on basic ASCII strings. Working with
strings in other alphabets, such as those with complex encodings, often involves
more advanced operations.
</div>


<h2>C# string initialization</h2>

<p>
There are multiple ways of creating strings, both immutable and mutable. We show
a few of them.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
using System.Text;

char[] cdb = ['M', 'y', 'S', 'q', 'l'];

string lang = "C#";
string ide = "NetBeans";
string db = new(cdb);

Console.WriteLine(lang);
Console.WriteLine(ide);
Console.WriteLine(db);

var sb1 = new StringBuilder(lang);
var sb2 = new StringBuilder();

sb2.Append("Fields");
sb2.Append(" of ");
sb2.Append("glory");

Console.WriteLine(sb1);
Console.WriteLine(sb2);
</pre>

<p>
The example shows a few ways of creating <code>System.String</code> and
<code>System.Text.StringBuilder</code> objects.
</p>

<pre class="explanation">
using System.Text;
</pre>

<p>
This statement enables to use the <code>System.Text.StringBuilder</code> type
without qualification.
</p>

<pre class="explanation">
string lang = "C#";
string ide = "NetBeans";
</pre>

<p>
The most common way is to create a string object from a string literal.
</p>

<pre class="explanation">
string db = new(cdb);
</pre>

<p>
Here we create a string object from an array of characters.
The <code>string</code> is an alias for the <code>System.String</code>.
</p>

<pre class="explanation">
var sb1 = new StringBuilder(lang);
</pre>

<p>
A <code>StringBuilder</code> object is created from a <code>String</code>.
</p>

<pre class="explanation">
var sb2 = new StringBuilder();

sb2.Append("Fields");
sb2.Append(" of ");
sb2.Append("glory");
</pre>

<p>
We create an empty <code>StringBuilder</code> object. We append three strings
into the object.
</p>

<pre class="compact">
$ dotnet run
C#
NetBeans
MySql
C#
Fields of glory
</pre>


<h2>C# string interpolation</h2>

<p>
The $ special character prefix identifies a string literal as an interpolated
string. An interpolated string is a string literal that might contain
interpolated expressions.
</p>

<p>
String formatting is a similar feature to string interpolation; it is covered
later in the chapter.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
int age = 23;
string name = "Peter";

DateTime now = DateTime.Now;

Console.WriteLine($"{name} is {age} years old");
Console.WriteLine($"Hello, {name}! Today is {now.DayOfWeek}, it's {now:HH:mm} now");
</pre>

<p>
The example presents C# string interpolation.
</p>

<pre class="explanation">
Console.WriteLine($"{name} is {age} years old");
</pre>

<p>
The interpolated variables are placed between {} brackets.
</p>

<pre class="explanation">
Console.WriteLine($"Hello, {name}! Today is {now.DayOfWeek}, it's {now:HH:mm} now");
</pre>

<p>
The interpolation syntax can receive expressions or formatting specifiers.
</p>

<pre class="compact">
$ dotnet run
Peter is 23 years old
Hello, Peter! Today is Friday, it's 12:23 now
</pre>


<h2>C# regular string</h2>

<p>
Regular strings can contain escape sequences, such as new line or tab character,
which are interpreted. Regular strings are placed between a pair of double
quotes.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
string s1 = "deep \t forest";
string s2 = "deep \n forest";

Console.WriteLine(s1);
Console.WriteLine(s2);

Console.WriteLine("C:\\Users\\Admin\\Documents");
</pre>

<p>
The example prints two strings which contain <code>\t</code> and
<code>\n</code> escape sequences.
</p>

<pre class="explanation">
Console.WriteLine("C:\\Users\\Admin\\Documents");
</pre>

<p>
When working with e.g. paths, the slashes must be escaped.
</p>

<pre class="compact">
$ dotnet run
deep     forest
deep
    forest
C:\Users\Admin\Documents
</pre>


<h2>C# verbatim string</h2>

<p>
Verbatim strings do not interprete escape sequences. Verbatim strings are
preceded with the <code>@</code> character. Verbatim strings can be used to work
with multiline strings.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
Console.WriteLine(@"deep \t forest");
Console.WriteLine(@"C:\Users\Admin\Documents");

var text = @"
    Not marble, nor the gilded monuments
Of princes, shall outlive this powerful rhyme;
But you shall shine more bright in these contents
Than unswept stone, besmeared with sluttish time.";

Console.WriteLine(text);
</pre>

<p>
In this code example we work with verbatim strings.
</p>

<pre class="explanation">
Console.WriteLine(@"deep \t forest");
</pre>

<p>
The <code>\t</code> special character is not interpreted; it is
only printed to the console.
</p>

<pre class="explanation">
Console.WriteLine(@"C:\Users\Admin\Documents");
</pre>

<p>
Verbatim strings are convenient when we work with paths; the shashes
do not have to be escaped.
</p>

<pre class="explanation">
var text = @"
    Not marble, nor the gilded monuments
Of princes, shall outlive this powerful rhyme;
But you shall shine more bright in these contents
Than unswept stone, besmeared with sluttish time.";
</pre>

<p>
Verbatim strings allow us to create multiline strings.
</p>

<pre class="compact">
$ dotnet run
deep \t forest
C:\Users\Admin\Documents

    Not marble, nor the gilded monuments
Of princes, shall outlive this powerful rhyme;
But you shall shine more bright in these contents
Than unswept stone, besmeared with sluttish time.
</pre>


<h2>C# strings are objects</h2>

<p>
Strings are objects. They are reference types. Strings are instances of
the <code>System.String</code> or <code>System.Text.StringBuilder</code> class.
Since they are objects, they have multiple methods available for doing various work.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
string lang = "Java";
string bclass = lang.GetType().Name;
Console.WriteLine(bclass);

string parclass = lang.GetType().BaseType!.Name;
Console.WriteLine(parclass);

if (lang.Equals(string.Empty))
{
    Console.WriteLine("The string is empty");
}
else
{
    Console.WriteLine("The string is not empty");
}

int len = lang.Length;
Console.WriteLine($"The string has {len} characters");
</pre>

<p>
In this program, we demonstrate that strings are objects. Objects must have a
class name, a parent class and they must also have some methods that we can call
or properties to access.
</p>

<pre class="explanation">
string lang = "Java";
</pre>

<p>
An object of <code>System.String</code> type is created.
</p>

<pre class="explanation">
string bclass = lang.GetType().Name;
Console.WriteLine(bclass);
</pre>

<p>
We determine the class name of the object to which the <code>lang</code>
variable refers.
</p>

<pre class="explanation">
string parclass = lang.GetType().BaseType!.Name;
Console.WriteLine(parclass);
</pre>

<p>
A parent class of our object is received. All objects have at least one parent —
the <code>Object</code>.
</p>

<pre class="explanation">
if (lang.Equals(string.Empty))
{
    Console.WriteLine("The string is empty");
} else
{
    Console.WriteLine("The string is not empty");
}
</pre>

<p>
Objects have various methods. With the <code>Equals</code> method we check if
the string is empty.
</p>

<pre class="explanation">
int len = lang.Length;
Console.WriteLine($"The string has {len} characters");
</pre>

<p>
The <code>Length</code> property returns the size of the string.
</p>

<pre class="compact">
$ dotnet run
String
Object
The string is not empty
The string has 4 characters
</pre>


<h2>C# mutable &amp; immutable strings</h2>

<p>
The <code>String</code> is a sequence of immutable characters, while the
<code>StringBuilder</code> is a sequence of mutable characters. The next
example shows the difference.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
using System.Text;

string name = "Jane";
string name2 = name.Replace('J', 'K');
string name3 = name2.Replace('n', 't');

Console.WriteLine(name);
Console.WriteLine(name3);

var sb = new StringBuilder("Jane");
Console.WriteLine(sb);

sb.Replace('J', 'K', 0, 1);
sb.Replace('n', 't', 2, 1);

Console.WriteLine(sb);
</pre>

<p>
Both objects have methods for replacing characters in a string.
</p>

<pre class="explanation">
string name = "Jane";
string name2 = name.Replace('J', 'K');
string name3 = name2.Replace('n', 't');
</pre>

<p>
Calling <code>Replace</code> method on a string results in returning a new
modified string. The original string is not changed.
</p>

<pre class="explanation">
sb.Replace('J', 'K', 0, 1);
sb.Replace('n', 't', 2, 1);
</pre>

<p>
The <code>Replace</code> method of a <code>StringBuilder</code> replaces a
character at the given index with a new character. The original string is
modified.
</p>

<pre class="compact">
$ dotnet run
Jane
Kate
Jane
Kate
</pre>


<h2>C# string concatenation</h2>

<p>
Immutable strings can be added using the + operator or the <code>Concat</code>
method. They form a new string which is a chain of all concatenated strings.
Mutable strings have the <code>Append</code> method which builds a string from
any number of other strings.
</p>

<p>
It is also possible to concatenate strings using string formatting and
interpolation.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
using System.Text;

Console.WriteLine("Return" + " of " + "the king.");
Console.WriteLine(string.Concat(string.Concat("Return", " of "), "the king."));

var sb = new StringBuilder();
sb.Append("Return");
sb.Append(" of ");
sb.Append("the king.");

Console.WriteLine(sb);

string s1 = "Return";
string s2 = "of";
string s3 = "the king.";

Console.WriteLine("{0} {1} {2}", s1, s2, s3);
Console.WriteLine($"{s1} {s2} {s3}");
</pre>

<p>
The example creates five sentences by concatenating strings.
</p>

<pre class="explanation">
Console.WriteLine("Return" + " of " + "the king.");
</pre>

<p>
A new string is formed by using the + operator.
</p>

<pre class="explanation">
Console.WriteLine(string.Concat(string.Concat("Return", " of "), "the king."));
</pre>

<p>
The <code>Concat</code> method concatenates two strings. The method is a static
method of the <code>System.String</code> class.
</p>

<pre class="explanation">
var sb = new StringBuilder();
sb.Append("Return");
sb.Append(" of ");
sb.Append("the king.");
</pre>

<p>
A mutable object of the <code>StringBuilder</code> type is created by calling
the <code>Append</code> method three times.
</p>

<pre class="explanation">
Console.WriteLine("{0} {1} {2}", s1, s2, s3);
</pre>

<p>
A string is formed with string formatting.
</p>

<pre class="explanation">
Console.WriteLine($"{s1} {s2} {s3}");
</pre>

<p>
Finally, the strings are added with the interpolation syntax.
</p>

<pre class="compact">
$ dotnet run
Return of the king.
Return of the king.
Return of the king.
Return of the king.
Return of the king.
</pre>


<h2>C# using quotes</h2>

<p>
When we want to display quotes, for instance in direct speech, the inner quotes
must be escaped.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
Console.WriteLine("There are many stars.");
Console.WriteLine("He said, \"Which one is your favourite?\"");

Console.WriteLine(@"
Lao Tzu has said:
""If you do not change direction, you may end up
where you are heading.""
");
</pre>

<p>
This example prints direct speech.
</p>

<pre class="explanation">
Console.WriteLine("He said, \"Which one is your favourite?\"");
</pre>

<p>
Inside a regular string, the character is escaped with <code>\</code>.
</p>

<pre class="explanation">
Console.WriteLine(@"
Lao Tzu has said:
""If you do not change direction, you may end up
where you are heading.""
");
</pre>

<p>
Inside a verbatim string, the quote is preceded with another quote.
</p>

<pre class="compact">
$ dotnet run
There are many stars.
He said, "Which one is your favourite?"

Lao Tzu has said:
"If you do not change direction, you may end up
where you are heading."
</pre>


<h2>C# comparing strings</h2>

<p>
We can compare two strings with the <code>==</code> operator.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
Console.WriteLine("12" == "12");
Console.WriteLine("17" == "9");
Console.WriteLine("aa" == "ab");
</pre>

<p>
In the example program, we compare strings.
</p>

<pre class="compact">
$ dotnet run
True
False
False
</pre>


<p>
The <code>string.Compare</code> method compares two specified strings and
returns an integer that indicates their relative position in the sort order. If
the returned value is less than zero, the first string is less than the second.
If it returns zero, both strings are equal. Finally, if the returned value is
greater than zero, the first string is greater than the second.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
string str1 = "ZetCode";
string str2 = "zetcode";

Console.WriteLine(string.Compare(str1, str2, true));
Console.WriteLine(string.Compare(str1, str2, false));
</pre>

<p>
There is an optional third <code>ignoreCase</code> argument. It determines if
the case should be honored or not.
</p>

<pre class="explanation">
Console.WriteLine(string.Compare(str1, str2, true));
</pre>

<p>
Compare two strings and ignore the case. This line prints 0 to the console.
</p>



<h2>C# string elements</h2>

<p>
A string is a sequence of characters. A character is a basic element of a
string.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
char[] crs = ['Z', 'e', 't', 'C', 'o', 'd', 'e'];
string s = new(crs);

char c1 = s[0];
char c2 = s[^1];

Console.WriteLine(c1);
Console.WriteLine(c2);

int i1 = s.IndexOf('e');
int i2 = s.LastIndexOf('e');

Console.WriteLine("The first index of character e is " + i1);
Console.WriteLine("The last index of character e is " + i2);

Console.WriteLine(s.Contains('t'));
Console.WriteLine(s.Contains('f'));

char[] elements = s.ToCharArray();

foreach (char e in elements)
{
    Console.WriteLine(e);
}
</pre>

<p>
In the first example, we work with an immutable string.
</p>

<pre class="explanation">
char[] crs = ['Z', 'e', 't', 'C', 'o', 'd', 'e'];
string s = new(crs);
</pre>

<p>
A new immutable string is formed from an array of characters.
</p>

<pre class="explanation">
char c1 = s[0];
char c2 = s[^1];
</pre>

<p>
Using the array access notation, we get the first and the last char value of the
string.
</p>

<pre class="explanation">
int i1 = s.IndexOf('e');
int i2 = s.LastIndexOf('e');
</pre>

<p>
With the above methods, we get the first and the last occurrence of the
character 'e'.
</p>

<pre class="explanation">
Console.WriteLine(s.Contains('t'));
Console.WriteLine(s.Contains('f'));
</pre>

<p>
With the <code>Contains</code> method we check if the string contains the 't'
character. The method returns a boolean value.
</p>

<pre class="explanation">
char[] elements = s.ToCharArray();

foreach (char e in elements)
{
    Console.WriteLine(e);
}
</pre>

<p>
The <code>ToCharArray</code> method creates a character array from the string.
We go through the array and print each of the characters.
</p>

<pre class="compact">
$ dotnet run
Z
e
The first index of character e is 1
The last index of character e is 6
True
False
Z
e
t
C
o
d
e
</pre>


<p>
In the second example, we work with the elements of a mutable string.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
using System.Text;

var sb = new StringBuilder("Misty mountains");
Console.WriteLine(sb);

sb.Remove(sb.Length-1, 1);
Console.WriteLine(sb);

sb.Append('s');
Console.WriteLine(sb);

sb.Insert(0, 'T');
sb.Insert(1, 'h');
sb.Insert(2, 'e');
sb.Insert(3, ' ');
Console.WriteLine(sb);

sb.Replace('M', 'm', 4, 1);
Console.WriteLine(sb);
</pre>

<p>
A mutable string is formed. We modify the contents of the string by deleting,
appending, inserting, and replacing characters.
</p>

<pre class="explanation">
sb.Remove(sb.Length-1, 1);
</pre>

<p>
This line deletes the last character.
</p>

<pre class="explanation">
sb.Append('s');
</pre>

<p>
The deleted character is appended back to the string.
</p>

<pre class="explanation">
sb.Insert(0, 'T');
sb.Insert(1, 'h');
sb.Insert(2, 'e');
sb.Insert(3, ' ');
</pre>

<p>
We insert four characters at the beginning of the string.
</p>

<pre class="explanation">
sb.Replace('M', 'm', 4, 1);
</pre>

<p>
Finally, we replace a character at index 4.
</p>

<pre class="compact">
$ dotnet run
Misty mountains
Misty mountain
Misty mountains
The Misty mountains
The misty mountains
</pre>


<h2>C# string Join and Split</h2>

<p>
The <code>Join</code> joins strings and the <code>Split</code> splits the
strings.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
string[] items = ["C#", "Visual Basic", "Java", "Perl"];

var langs = string.Join(",", items);
Console.WriteLine(langs);

string[] langs2 = langs.Split(',');

foreach (string lang in langs2)
{
    Console.WriteLine(lang);
}
</pre>

<p>
In the program we join and split strings.
</p>

<pre class="explanation">
string[] items = ["C#", "Visual Basic", "Java", "Perl"];
</pre>

<p>
This is an array of strings. These strings are going to be joined.
</p>

<pre class="explanation">
string langs = string.Join(",", items);
</pre>

<p>
All words from the array are joined. We build one string from them. There will
be a comma character between each two words.
</p>

<pre class="explanation">
string[] langs2 = langs.Split(',');
</pre>

<p>
As a reverse operation, we split the langs string. The <code>Split</code> method
returns an array of words, delimited by a character. In our case it is a comma
character.
</p>

<pre class="explanation">
foreach (string lang in langs2)
{
    Console.WriteLine(lang);
}
</pre>

<p>
We go through the array and print its elements.
</p>

<pre class="compact">
$ dotnet run
C#,Visual Basic,Java,Perl
C#
Visual Basic
Java
Perl
</pre>


<h2>C# string StartsWith</h2>

<p>
The <code>StartsWith</code> method determines whether this string instance
starts with the specified character.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
var words = "club\nsky\nblue\ncup\ncoin\nnew\ncent\nowl\nfalcon\nwar\nice";

using var sr = new StringReader(words);

string? line;

while ((line = sr.ReadLine()) != null)
{
    if (line.StartsWith('c')) 
    {
        Console.WriteLine(line);
    }
}
</pre>

<p>
We have a couple of words in a string. We print all words that start with letter
c. 
</p>

<pre class="compact">
$ dotnet run
club
cup
coin
cent
</pre>


<h2>C# string EndsWith</h2>

<p>
The <code>EndsWith</code> determines whether the end of this string instance
matches a specified string.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
var words = "club\nsky\nblue\ncup\ncoin\nnew\ncent\nowl\nfalcon\nwar\nice";

using var sr = new StringReader(words);

string? line;

while ((line = sr.ReadLine()) != null)
{
    if (line.EndsWith('y') || line.EndsWith('n')) 
    {
        Console.WriteLine(line);
    }
}
</pre>

<p>
In the example, we print all words that end either with n or y. 
</p>


<pre class="compact">
$ dotnet run
sky
coin
falcon
</pre>


<h2>C# string ToUpper/ToLower</h2>

<p>
The <code>ToUpper</code> method converts all of the characters of the string to
upper case. The <code>ToLower</code> method converts all of the characters of
the string to lower case. 
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
var word1 = "Cherry";

var u_word1 = word1.ToUpper();
var l_word1 = u_word1.ToLower();

Console.WriteLine(u_word1);
Console.WriteLine(l_word1);

var word2 = "Čerešňa";

var u_word2 = word2.ToUpper();
var l_word2 = u_word2.ToLower();

Console.WriteLine(u_word2);
Console.WriteLine(l_word2);
</pre>

<p>
We modify the case of two words. 
</p>

<pre class="compact">
$ dotnet run
CHERRY
cherry
ČEREŠŇA
čerešňa
</pre>


<h2>Working with C# Runes</h2>

<p>
The <code>EnumerateRunes</code> method in C# allows you to iterate over
individual Unicode characters, or "runes," within a string. A rune is
represented by the <code>System.Text.Rune</code> type, which corresponds to a
single Unicode scalar value, enabling efficient handling of text containing
characters from diverse alphabets, symbols, or emojis.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
var text = "🐄🦙🐘🐫🐑🦝🦍🐯";
var runes = text.EnumerateRunes();

foreach (var rune in runes) 
{
    Console.WriteLine(rune);
}
</pre>

<p>
In this example, we use the <code>EnumerateRunes</code> method to iterate over a
sequence of emojis. This approach ensures that multi-byte Unicode characters are
accurately processed, preserving their integrity and proper representation.
</p>

<pre class="compact">
$ dotnet run
🐄
🦙
🐘
🐫
🐑
🦝
🦍
🐯
</pre>



<h2>C# string Remove</h2>

<p>
The <code>Remove</code> method returns a new string in which a specified number
of characters from the current string are deleted.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
var text = "Did you go there? We did, but we had a \"great\" service there.";

string[] parts = text.Split(" ");

foreach (var part in parts)
{
    var word = removeChars(part);
    Console.WriteLine(word);
}

string removeChars(string part)
{
    var word = part;

    if (part.EndsWith('.') || part.EndsWith('?') || 
        part.EndsWith(',') || part.EndsWith('\"'))
    {
        word = part.Remove(part.Length - 1, 1);
    }

    if (word.StartsWith('\"'))
    {
        word = word.Remove(0, 1);
    }

    return word;
}
</pre>

<p>
The example splits a string into words and removes potential commas, dots,
question marks, or double quotation marks. 
</p>

<pre class="explanation">
if (part.EndsWith('.') || part.EndsWith('?') || 
    part.EndsWith(',') || part.EndsWith('\"'))
{
    word = part.Remove(part.Length - 1, 1);
}
</pre>

<p>
If the current word ends with any of the characters, we remove it with
<code>Remove</code>.
</p>

<pre class="explanation">
if (word.StartsWith('\"'))
{
    word = word.Remove(0, 1);
}
</pre>

<p>
Also, we remove the double quote character if it precedes the string.
</p>

<pre class="compact">
$ dotnet run
Did
you
go
there
We
did
but
we
had
a
great
service
there
</pre>


<h2>C# Substring</h2>

<p>
The <code>Substring</code> method retrieves a substring from a string.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
var word = "bookcase";

Console.WriteLine(word.Substring(0, 4));
Console.WriteLine(word.Substring(4, 4));
Console.WriteLine(word.Substring(4));
</pre>

<p>
The example uses the substring method to create two substrings. 
</p>

<pre class="explanation">
Console.WriteLine(word.Substring(0, 4));
</pre>

<p>
We get the first word from the string. The first paramenter is the starting 
index and the second is the length of the substring.
</p>

<pre class="explanation">
Console.WriteLine(word.Substring(4, 4));
</pre>

<p>
We get the second word.
</p>

<pre class="explanation">
Console.WriteLine(word.Substring(4));
</pre>

<p>
This overloaded method starts from the specified index and continues to the end
of the string.
</p>

<pre class="compact">
$ dotnet run
book
case
case
</pre>


<h2>C# string Palindrome</h2>

<p>
A palindrome is a word, number, phrase, or other sequence of characters which
reads the same backward as forward, such as madam or racecar. There are many
ways to check if a string is a palindrome. The following example is one of the
possible solutions. 
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
Console.WriteLine(isPalindrome("radar"));
Console.WriteLine(isPalindrome("kayak"));
Console.WriteLine(isPalindrome("forest"));

bool isPalindrome(string original)
{
    char[] data = original.ToCharArray();

    int i = 0;
    int j = data.Length - 1;

    while (j &gt; i)
    {

        if (data[i] != data[j])
        {
            return false;
        }

        i++;
        j--;
    }

    return true;
}
</pre>

<p>
We have an implementation of the isPalindrome method. 
</p>

<pre class="explanation">
char[] data = original.ToCharArray();
</pre>

<p>
We turn the string into a array of characters. 
</p>

<pre class="explanation">
int i = 0;
int j = data.Length - 1;

while (j &gt; i)
{
    if (data[i] != data[j])
    {
        return false;
    }

    i++;
    j--;
}

return true;
</pre>

<p>
We iterate through the array and compare the left side characters with the right
side corresponding characters. If all match, we return true, otherwise we return
false. 
</p>

<pre class="compact">
$ dotnet run
True
True
False
</pre>



<h2>C# string Copy vs Clone</h2>

<p>
We describe a difference between two methods: <code>Copy</code>
and <code>Clone</code>. The <code>Copy</code> method creates a new instance of
string with the same value as a specified string. The <code>Clone</code> method
returns a reference to the string which is being cloned. It is not an
independent copy of the string on the Heap. It is another reference on the same
string.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
string str = "ZetCode";

string cloned = (string) str.Clone();
string copied = string.Copy(str);

Console.WriteLine(str.Equals(cloned)); // prints True
Console.WriteLine(str.Equals(copied)); // prints True

Console.WriteLine(ReferenceEquals(str, cloned)); // prints True
Console.WriteLine(ReferenceEquals(str, copied)); // prints False
</pre>

<p>
Our example demonstrates the difference between the two methods.
</p>

<pre class="explanation">
string cloned = (string) str.Clone();
string copied = string.Copy(str);
</pre>

<p>
The string value is cloned and copied.
</p>

<pre class="explanation">
Console.WriteLine(str.Equals(cloned)); // prints True
Console.WriteLine(str.Equals(copied)); // prints True
</pre>

<p>
The <code>Equals</code> method determines whether two string objects have the
same value. The contents of all three strings are the same.
</p>

<pre class="explanation">
Console.WriteLine(ReferenceEquals(str, cloned)); // prints True
Console.WriteLine(ReferenceEquals(str, copied)); // prints False
</pre>

<p>
The <code>ReferenceEquals</code> method compares the two reference objects.
Therefore comparing a copied string to the original string returns false.
Because they are two distinct objects.
</p>


<h2>C# string format</h2>

<p>
In the next examples, we format strings. More in-depth coverage is presented in 
<a href="/csharp/stringformat">C# String Format</a> article.
</p>


<p>
The .NET platform has a feature called <em>composite formatting</em>. It is
supported by <code>Format</code> and <code>WriteLine</code> methods. A method
takes a list of objects and a composite format string as input. The format
string consists of fixed string and some format items. These format items are
indexed placeholders which correspond to the objects in the list.
</p>

<p>
The format item has the following syntax:
</p>

<pre class="compact">
{index[,length][:formatString]}
</pre>

<p>
The index component is mandatory. It is a number starting from 0 that refers
to an item from the list of objects. Multiple items can refer to the same element
of the list of objects. An object is ignored if it is not referenced by a format
item. If we refer outside the bounds of the list of objects, a runtime exception
is thrown.
</p>

<p>
The length component is optional. It is the minimum number of characters in
the string representation of the parameter. If positive, the parameter is
right-aligned; if negative, it is left-aligned. If it is specified,
there must by a colon separating the index and the length.
</p>

<p>
The formatString is optional. It is a string that formats a value is a
specific way. It can be used to format dates, times, numbers or enumerations.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
int oranges = 2;
int apples = 4;
int bananas = 3;

string str1 = "There are {0} oranges, {1} apples and {2} bananas";
string str2 = "There are {1} oranges, {2} bananas and {0} apples";

Console.WriteLine(str1, oranges, apples, bananas);
Console.WriteLine(str2, apples, oranges, bananas);
</pre>

<p>
We print a simple message to the console. We use only index component
of the format item.
</p>

<pre class="explanation">
string str1 = "There are {0} oranges, {1} apples and {2} bananas";
</pre>

<p>
The <code>{0}</code>, <code>{1}</code>, and <code>{2}</code> are format
items. We specify the index component. Other components are optional.
</p>

<pre class="explanation">
Console.WriteLine(str1, oranges, apples, bananas);
</pre>

<p>
Now we put together the composite formatting. We have the string and
the list of objects (oranges, apples, bananas). The <code>{0}</code> format item
refers to the oranges. The <code>WriteLine</code> method
replaces the <code>{0}</code> format item with the contents of the oranges
variable.
</p>

<pre class="explanation">
string str2 = "There are {1} oranges, {2} bananas and {0} apples";
</pre>

<p>
The order of the format items referring to the objects is notation
important.
</p>

<pre class="compact">
$ dotnet run
There are 2 oranges, 4 apples and 3 bananas
There are 2 oranges, 3 bananas and 4 apples
</pre>

<p>
The next example formats numeric data.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
Console.WriteLine("{0}  {1, 12}", "Decimal", "Hexadecimal");

Console.WriteLine("{0:D}  {1,8:X}", 502, 546);
Console.WriteLine("{0:D}  {1,8:X}", 345, 765);
Console.WriteLine("{0:D}  {1,8:X}", 320, 654);
Console.WriteLine("{0:D}  {1,8:X}", 120, 834);
Console.WriteLine("{0:D}  {1,8:X}", 620, 454);
</pre>

<p>
We print numbers in a decimal and hexadecimal format. We also align the numbers
using the length component.
</p>

<pre class="explanation">
Console.WriteLine("{0:D}  {1,8:X}", 502, 546);;
</pre>

<p>
The <code>{0:D}</code> format item specifies, the first item from the
list of supplied objects will be taken and formatted in
the decimal format. The <code>{1,8:X}</code> format item takes the
second item. Formats it in the hexadecimal format <code>:X</code>.
And the string length will be 8 characters <code>8 </code>. Because the
number has only three characters, it is right aligned and
padded with empty strings.
</p>

<pre class="compact">
$ dotnet run
Decimal   Hexadecimal
502       222
345       2FD
320       28E
120       342
620       1C6
</pre>


<p>
The last two examples format numeric and date data.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
Console.WriteLine(string.Format("Number: {0:N}", 126));
Console.WriteLine(string.Format("Scientific: {0:E}", 126));
Console.WriteLine(string.Format("Currency: {0:C}", 126));
Console.WriteLine(string.Format("Percent: {0:P}", 126));
Console.WriteLine(string.Format("Hexadecimal: {0:X}", 126));
</pre>

<p>
The example demonstrates the standard formatting specifiers for numbers.
Number 126 is printed in five different formats: normal, scientific, currency,
percent and hexadecimal.
</p>

<pre class="compact">
$ dotnet run
Number: 126.00
Scientific: 1.260000E+002
Currency: $126.00
Percent: 12,600.00%
Hexadecimal: 7E
</pre>


<p>
Finally, we format date and time data.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
DateTime today = DateTime.Now;

Console.WriteLine(string.Format("Short date: {0:d}", today));
Console.WriteLine(string.Format("Long date: {0:D}", today));
Console.WriteLine(string.Format("Short time: {0:t}", today));
Console.WriteLine(string.Format("Long time: {0:T}", today));
Console.WriteLine(string.Format("Month: {0:M}", today));
Console.WriteLine(string.Format("Year: {0:Y}", today));
</pre>

<p>
The code example shows six various formats for current date and time.
</p>

<pre class="compact">
$ dotnet run
Short date: 5/1/2025
Long date: Thursday, May 1, 2025
Short time: 5:13 PM
Long time: 5:13:30 PM
Month: May 1
Year: May 2025
</pre>



<h2>Trimming whitespace</h2>

<p>
The <code>Trim</code>, <code>TrimStart</code>, and <code>TrimEnd</code>
methods are used to remove whitespace characters from the beginning and/or end
of a string. The <code>Trim</code> method removes whitespace from both ends,
while <code>TrimStart</code> removes whitespace from the beginning and
<code>TrimEnd</code> removes whitespace from the end. These methods return a
new string with the specified characters removed, leaving the original string
unchanged.  
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
string input = "   hello there   ";

Console.WriteLine($"Original: '{input}'");
Console.WriteLine($"Trim: '{input.Trim()}'");
Console.WriteLine($"TrimStart: '{input.TrimStart()}'");
Console.WriteLine($"TrimEnd: '{input.TrimEnd()}'");
</pre>

<p>
This example shows how to remove whitespace from the beginning and/or end of a
string using <code>Trim</code>, <code>TrimStart</code>, and
<code>TrimEnd</code>.
</p>

<h2>String comparison with culture and case sensitivity</h2>

<p>
The <code>String.Compare</code> method is used to compare two strings
with different <code>StringComparison</code> options. The <code>StringComparison</code>
enum provides options for culture-sensitive and case-sensitive comparisons.
The <code>StringComparison.Ordinal</code> option performs a case-sensitive
ordinal comparison, while <code>StringComparison.InvariantCultureIgnoreCase</code>
performs a case-insensitive comparison using the invariant culture. 
</p>

<p>
This is useful for comparing strings in a way that is not affected by the
current culture settings of the system. The <code>String.Compare</code> method
returns an integer indicating the relative position of the two strings in the
sort order. A negative value indicates that the first string precedes the second
string, zero indicates that they are equal, and a positive value indicates that
the first string follows the second string.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
string a = "straße";
string b = "STRASSE";

Console.WriteLine(string.Compare(a, b, StringComparison.Ordinal));
Console.WriteLine(string.Compare(a, b, StringComparison.InvariantCultureIgnoreCase));
</pre>

<p>
This example demonstrates comparing strings with different
<code>StringComparison</code> options, showing the effect of culture and case
sensitivity.
</p>

<h2>Replace and remove substrings</h2>

<p>
The <code>Replace</code> method is used to replace all occurrences of a
specified substring with another substring in a string. The <code>Remove</code>
method is used to remove a specified number of characters from a string,
starting at a specified index. Both methods return a new string with the
modifications applied, leaving the original string unchanged. 
</p>

<p>
The <code>Replace</code> method is useful for changing specific parts of a
string, while the <code>Remove</code> method is useful for deleting unwanted
characters or substrings. The <code>Remove</code> method takes two parameters:
the starting index and the number of characters to remove. The
<code>Replace</code> method takes two parameters: the substring to replace and
the new substring to insert. Both methods return a new string with the specified
modifications, leaving the original string unchanged.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
string text = "The quick brown fox jumps over the lazy dog.";
string replaced = text.Replace("fox", "cat");
string removed = text.Remove(16, 4); // removes 'fox '

Console.WriteLine(replaced);
Console.WriteLine(removed);
</pre>

<p>
This example shows how to replace a substring and remove a portion of a string
by index and length.
</p>

<h2>PadLeft and PadRight for formatting</h2>

<p>
The <code>PadLeft</code> and <code>PadRight</code> methods are used to
pad a string with a specified character to the left or right, respectively.
The <code>PadLeft</code> method adds padding characters to the left side of
the string until it reaches a specified total width, while the
<code>PadRight</code> method adds padding characters to the right side of
the string. 
</p>

<p>
Both methods return a new string with the padding applied, leaving the original
string unchanged. The padding character can be specified as an argument, and the
total width can be specified as well. If the original string is already equal to
or greater than the specified width, no padding is added. These methods are
useful for formatting strings for display, such as aligning text in a table or
ensuring consistent widths for output.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
string word = "42";

Console.WriteLine(word.PadLeft(5, '0'));
Console.WriteLine(word.PadRight(8, '-'));
</pre>

<p>
This example demonstrates how to align or pad strings using
<code>PadLeft</code> and <code>PadRight</code>.
</p>

<h2>Efficient string search with IndexOf and LastIndexOf</h2>

<p>
The <code>IndexOf</code> and <code>LastIndexOf</code> methods are used to
find the position of a specified character or substring within a string.
The <code>IndexOf</code> method returns the zero-based index of the first
occurrence of the specified character or substring, while the
<code>LastIndexOf</code> method returns the zero-based index of the last
occurrence. If the specified character or substring is not found, both
methods return -1. 
</p>

<p>
These methods are useful for searching for specific
characters or substrings within a larger string, allowing you to determine
the position of the first or last occurrence. The search is case-sensitive
by default, but you can specify a <code>StringComparison</code> option to
control the case sensitivity of the search. The <code>IndexOf</code> and
<code>LastIndexOf</code> methods can also take additional parameters to
specify the starting index and the number of characters to search within.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
string phrase = "abracadabra";
int first = phrase.IndexOf('a');
int last = phrase.LastIndexOf('a');

Console.WriteLine($"First 'a': {first}");
Console.WriteLine($"Last 'a': {last}");
</pre>

<p>
This example uses <code>IndexOf</code> and <code>LastIndexOf</code> to find
the position of characters in a string.
</p>


<h2>Source</h2>

<p>
<a href="https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/strings/">Strings and string literals</a>
</p>

<p>
In this article, we explored the fundamentals of C# strings, including their
definition, key classes, and practical usage. By understanding how strings
function in C#, you can effectively handle and manipulate text in your
applications, whether you're working with immutable objects or dynamic string
builders.
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
<span>&copy; 2007 - 2023 Jan Bodnar</span>
<span>admin(at)zetcode.com</span>
</div>

</footer>


<script src="/cfg/utils.js"></script>
</body>
</html>

