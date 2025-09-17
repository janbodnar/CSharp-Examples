
<!DOCTYPE html>
<html lang="en">
<head>
<title>C# operator - working with C# operators and expressions</title>
<link rel="stylesheet" href="/cfg/style.css" type="text/css">
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="keywords" content="C#, operators, programming, language, .NET, learn C#">
<meta name="description" content="C# operator tutorial covers operators and
expressions of the C# language. Expressions are constructed from operands and
operators. The operators of an expression indicate which operations to apply to
the operands.">

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


<h1>C# operator</h1>

<p class="last_mod">
last modified July 5, 2023
</p>
 
<p>
In this article we cover C# operators.
</p>

<p>
Expressions are constructed from operands and operators. The operators of an
expression indicate which operations to apply to the operands. The order of
evaluation of operators in an expression is determined by the
<em>precedence</em> and <em>associativity</em> of the operators.
</p>

<p>
An <em>operator</em> is a special symbol which indicates a certain process is
carried out. Operators in programming languages are taken from mathematics.
Programmers work with data. The operators are used to process data. An
<em>operand</em> is one of the inputs (arguments) of an operator.
</p>



<h2>C# operator list</h2>

<p>
The following table shows a set of operators used in the C# language.
</p>

<table>
  <tr>
    <th>Category</th>
    <th>Symbol</th>
  </tr>
  <tr>
    <td>Sign operators</td>
    <td><code>+   -</code></td>
  </tr>
  <tr>
    <td>Arithmetic</td>
    <td><code>+   -   *   /   %</code></td>
  </tr>
  <tr>
    <td>Logical (boolean and bitwise)</td>
    <td><code>&amp;   |   ^   !   ~   &amp;&amp;   ||   true   false</code></td>
  </tr>
  <tr>
    <td>String concatenation</td>
    <td><code>+</code></td>
  </tr>
  <tr>
    <td>Increment, decrement</td>
    <td><code>++ --</code></td>
  </tr>
  <tr>
    <td>Shift</td>
    <td><code>&lt;&lt; &gt;&gt;</code></td>
  </tr>
  <tr>
    <td>Relational</td>
    <td><code>==   !=   &lt;   &gt;   &lt;=   &gt;=</code></td>
  </tr>
  <tr>
    <td>Assignment</td>
    <td><code>=   +=   -=   *=   /=   %=  &amp;=  |=   ^=  ??=  &lt;&lt;=   &gt;&gt;= </code></td>
  </tr>
  <tr>
    <td>Member access</td>
    <td><code>.  ?.</code></td>
  </tr>
  <tr>
    <td>Indexing</td>
    <td><code>[]  ?[]</code></td>
  </tr>
  <tr>
    <td>Cast</td>
    <td><code></code></td>
  </tr>
  <tr>
    <td>Ternary</td>
    <td><code>?:</code></td>
  </tr>
  <tr>
    <td>Delegate concatenation and removal</td>
    <td><code>+  -</code></td>
  </tr>
  <tr>
    <td>Object creation</td>
    <td><code>new</code></td>
  </tr>
  <tr>
    <td>Type information</td>
    <td><code>as   is   sizeof   typeof   </code></td>
  </tr>
  <tr>
    <td>Overflow exception control</td>
    <td><code>checked unchecked</code></td>
  </tr>
  <tr>
    <td>Indirection and address</td>
    <td><code>*   -&gt;   []   &amp;</code></td>
  </tr>
  <tr>
    <td>Lambda</td>
    <td><code>=&gt;</code></td>
  </tr>
</table>

<p>
An operator usually has one or two operands. Those operators that work
with only one operand are called <em>unary operators</em>.
Those who work with two operands are called <em>binary operators</em>.
There is also one ternary operator <code>?:</code>, which works with three operands.
</p>

<p>
Certain operators may be used in different contexts. For example the + operator.
From the above table we can see that it is used in different cases.
It adds numbers, concatenates strings or delegates; indicates the sign
of a number. We say that the operator is <em>overloaded</em>.
</p>

<h2>C# unary operators</h2>

<p>
C# unary operators include: +, -, ++, --, cast operator (), and negation !.
</p>

<h3>C# sign operators</h3>

<p>
There are two sign operators: <code>+</code> and <code>-</code>. They are
used to indicate or change the sign of a value.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
Console.WriteLine(2);
Console.WriteLine(+2);
Console.WriteLine(-2);
</pre>

<p>
The <code>+</code> and <code>-</code> signs indicate the sign of a value.
The plus sign can be used to indicate that we have a positive number. It can be
omitted and it is mostly done so.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
int a = 1;
Console.WriteLine(-a);
Console.WriteLine(-(-a));
</pre>

<p>
The minus sign changes the sign of a value.
</p>

<pre class="compact">
$ dotnet run
-1
1
</pre>


<h3>C# increment and decrement operators</h3>

<p>
Incrementing or decrementing a value by one is a common task in
programming. C# has two convenient operators for this: <code>++</code>
and <code>--</code>.
</p>

<pre class="compact">
x++;
x = x + 1;
...
y--;
y = y - 1;
</pre>

<p>
The above two pairs of expressions do the same.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
int x = 6;

x++;
x++;

Console.WriteLine(x);

x--;
Console.WriteLine(x);
</pre>

<p>
In the above example, we demonstrate the usage of both operators.
</p>

<pre class="explanation">
int x = 6;

x++;
x++;
</pre>

<p>
We initiate the <code>x</code> variable to 6. Then we increment
<code>x</code> two times. Now the variable equals to 8.
</p>

<pre class="explanation">
x--;
</pre>

<p>
We use the decrement operator. Now the variable equals to 7.
</p>

<pre class="compact">
$ dotnet run
8
7
</pre>

<h3>C# explicit cast operator</h3>

<p>
The explicit cast operator () can be used to cast a type to
another type. Note that this operator works only on certain types.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
float val = 3.2f;
int num = (int) val;

Console.WriteLine(num);
</pre>

<p>
In the example, we explicitly cast a <code>float</code> type to <code>int</code>.
</p>


<h3>Negation operator</h3>

<p>
The negation operator (!) reverses the meaning of its operand.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
var isValid = false;

if (!isValid)
{
    Console.WriteLine("The option is not valid");
}
</pre>

<p>
In the example, we build a negative condition: it is executed if the inverse
of the expression is valid.
</p>


<h2>C# assignment operator</h2>

<p>
The assignment operator <code>=</code> assigns a value to a variable.
A <em>variable</em> is a placeholder for a value. In mathematics, the
<code>=</code> operator has a different meaning. In an equation, the
<code>=</code> operator is an equality operator. The left
side of the equation is equal to the right one.
</p>

<pre class="compact">
int x = 1;
</pre>

<p>
Here we assign a number to the <code>x</code> variable.
</p>

<pre class="compact">
x = x + 1;
</pre>

<p>
The previous expression does not make sense in mathematics. But it is
legal in programming. The expression adds 1 to the <code>x</code>
variable. The right side is equal to 2 and 2 is assigned to <code>x</code>.
</p>

<pre class="compact">
3 = x;
</pre>

<p>
This code example results in syntax error. We cannot assign a value to
a literal.
</p>


<h2>C# concatenating strings</h2>

<p>
The + operator is also used to concatenate strings.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
Console.WriteLine("Return " + "of " + "the king.");
</pre>

<p>
We join three strings together using string concatenation operator.
</p>

<pre class="compact">
$ dotnet run
Return of the king.
</pre>


<h2>C# arithmetic operators</h2>

<p>
The following is a table of arithmetic operators in C#.
</p>

<table>
<tr>
<th>Symbol</th><th>Name</th>
</tr>
<tr><td><code>+</code></td><td>Addition</td></tr>
<tr><td><code>-</code></td><td>Subtraction</td></tr>
<tr><td><code>*</code></td><td>Multiplication</td></tr>
<tr><td>/</td><td>Division</td></tr>
<tr><td><code>%</code></td><td>Remainder</td></tr>
</table>

<p>
The following example shows arithmetic operations.
</p>

<div class="codehead">Project.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
int a = 10;
int b = 11;
int c = 12;

int add = a + b + c;
int sb = c - a;
int mult = a * b;
int div = c / 3;
int rem = c % a;

Console.WriteLine(add);
Console.WriteLine(sb);
Console.WriteLine(mult);
Console.WriteLine(div);
Console.WriteLine(rem);
</pre>

<p>
In the preceding example, we use addition, subtraction, multiplication,
division, and remainder operations. This is all familiar from the mathematics.
</p>

<pre class="explanation">
int rem = c % a;
</pre>

<p>
The <code>%</code> operator is called the remainder or the modulo operator.
It finds the remainder of division of one number by another. For example,
<code>9 % 4</code>, 9 modulo 4 is 1, because 4 goes into 9 twice with a
remainder of 1.
</p>

<pre class="compact">
$ dotnet run
33
2
110
4
2
</pre>

<p>
Next we show the distinction between integer and floating point division.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
int c = 5 / 2;
Console.WriteLine(c);

double d = 5 / 2.0;
Console.WriteLine(d);
</pre>

<p>
In the preceding example, we divide two numbers.
</p>

<pre class="explanation">
int c = 5 / 2;
Console.WriteLine(c);
</pre>

<p>
In this code, we have done integer division. The returned value
of the division operation is an integer. When we divide two integers
the result is an integer.
</p>

<pre class="explanation">
double d = 5 / 2.0;
Console.WriteLine(d);
</pre>

<p>
If one of the values is a double or a float, we perform a
floating point division. In our case, the second operand
is a double so the result is a double.
</p>

<pre class="compact">
$ dotnet run
2
2.5
</pre>


<h2>C# Boolean operators</h2>

<p>
In C#, we have three logical operators. The <code>bool</code> keyword is
used to declare a Boolean value.
</p>

<table>
<tr>
<th>Symbol</th><th>Name</th>
</tr>
<tr><td><code>&amp;&amp;</code></td><td>logical and</td></tr>
<tr><td><code>||</code></td><td>logical or</td></tr>
<tr><td><code>!</code></td><td>negation</td></tr>
</table>

<p>
Boolean operators are also called logical.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
int x = 3;
int y = 8;

Console.WriteLine(x == y);
Console.WriteLine(y &gt; x);

if (y &gt; x)
{
    Console.WriteLine("y is greater than x");
}
</pre>

<p>
Many expressions result in a boolean value. Boolean values are used
in conditional statements.
</p>

<pre class="explanation">
Console.WriteLine(x == y);
Console.WriteLine(y &gt; x);
</pre>

<p>
Relational operators always result in a boolean value. These two lines
print false and true.
</p>

<pre class="explanation">
if (y &gt; x)
{
    Console.WriteLine("y is greater than x");
}
</pre>

<p>
The body of the <code>if</code> statement is executed only if the condition
inside the parentheses is met. The <code>y > x</code> returns true, so the message
"y is greater than x" is printed to the terminal.
</p>

<p>
The <code>true</code> and <code>false</code> keywords represent boolean
literals in C#.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
bool a = true &amp;&amp; true;
bool b = true &amp;&amp; false;
bool c = false &amp;&amp; true;
bool d = false &amp;&amp; false;

Console.WriteLine(a);
Console.WriteLine(b);
Console.WriteLine(c);
Console.WriteLine(d);
</pre>

<p>
Example shows the logical and operator.
It evaluates to true only if both operands are true.
</p>

<pre class="compact">
$ dotnet run
True
False
False
False
</pre>

<p>
Only one expression results in <code>True</code>.
</p>

<p>
The logical or <code>||</code> operator evaluates to true,
if either of the operands is true.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
bool a = true || true;
bool b = true || false;
bool c = false || true;
bool d = false || false;

Console.WriteLine(a);
Console.WriteLine(b);
Console.WriteLine(c);
Console.WriteLine(d);
</pre>

<p>
If one of the sides of the operator is true, the outcome of
the operation is true.
</p>

<pre class="compact">
$ dotnet run
True
True
True
False
</pre>

<p>
Three of four expressions result in true.
</p>

<p>
The negation operator <code>!</code> makes true false and false true.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
Console.WriteLine(!true);
Console.WriteLine(!false);
Console.WriteLine(!(4 &lt; 3));
</pre>

<p>
The example shows the negation operator in action.
</p>

<pre class="compact">
$ dotnet run
False
True
True
</pre>


<p>
The <code>||</code>, and <code>&amp;&amp;</code> operators
are short circuit evaluated. <em>Short circuit evaluation</em> means
that the second argument is only evaluated if the first argument does not
suffice to determine the value of the expression: when the first argument of the
logical and evaluates to false, the overall value must be false; and when the
first argument of logical or evaluates to true, the overall value must be true.
Short circuit evaluation is used mainly to improve performance.
</p>

<p>
An example may clarify this a bit more.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
Console.WriteLine("Short circuit");

if (One() &amp;&amp; Two())
{
    Console.WriteLine("Pass");
}

Console.WriteLine("#############");

if (Two() || One())
{
    Console.WriteLine("Pass");
}

bool One()
{
    Console.WriteLine("Inside one");

    return false;
}

bool Two()
{
    Console.WriteLine("Inside two");

    return true;
}
</pre>

<p>
We have two methods in the example. They are used as operands in boolean
expressions. 
</p>

<pre class="explanation">
if (One() &amp;&amp; Two())
{
    Console.WriteLine("Pass");
}
</pre>

<p>
The <code>One</code> method returns <code>false</code>. The short circuit
&amp;&amp; does not evaluate the second method. It is not necessary. Once an
operand is <code>false</code>, the result of the logical conclusion is always
<code>false</code>. Only "Inside one" is only printed to the console.
</p>

<pre class="explanation">
Console.WriteLine("#############");

if (Two() || One())
{
    Console.WriteLine("Pass");
}
</pre>

<p>
In the second case, we use the <code>||</code> operator and use the
<code>Two</code> method as the first operand. In this case, "Inside two" and
"Pass" strings are printed to the terminal. It is again not necessary to
evaluate the second operand, since once the first operand evaluates to
<code>true</code>, the logical or is always <code>true</code>.
</p>

<pre class="compact">
$ dotnet run
Short circuit
Inside one
#############
Inside two
Pass
</pre>


<h2>C# relational operators</h2>

<p>
Relational operators are used to compare values. These operators always
result in boolean value.
</p>

<table>
<tr>
<th>Symbol</th><th>Meaning</th>
</tr>
<tr><td><code>&lt;</code></td><td>less than</td></tr>
<tr><td><code>&lt;=</code></td><td>less than or equal to</td></tr>
<tr><td><code>&gt;</code></td><td>greater than</td></tr>
<tr><td><code>&gt;=</code></td><td>greater than or equal to</td></tr>
<tr><td><code>==</code></td><td>equal to</td></tr>
<tr><td><code>!=</code></td><td>not equal to</td></tr>
</table>

<p>
Relational operators are also called comparison
operators.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
Console.WriteLine(3 &lt; 4);
Console.WriteLine(3 == 4);
Console.WriteLine(4 &gt;= 3);
Console.WriteLine(4 != 3);
</pre>

<p>
In the code example, we have four expressions. These expressions compare integer
values. The result of each of the expressions is either true or false.
In C# we use <code>==</code> to compare numbers. Some languages
like Ada, Visual Basic, or Pascal use <code>=</code> for comparing numbers.
</p>


<h2>C# bitwise operators</h2>

<p>
Decimal numbers are natural to humans. Binary numbers are native to computers.
Binary, octal, decimal, or hexadecimal symbols are only notations of the same
number. Bitwise operators work with bits of a binary number. Bitwise operators
are seldom used in higher level languages like C#.
</p>

<table>
<tr>
<th>Symbol</th><th>Meaning</th>
</tr>
<tr><td><code>~</code></td><td>bitwise negation</td></tr>
<tr><td><code>^</code></td><td>bitwise exclusive or</td></tr>
<tr><td><code>&amp;</code></td><td>bitwise and</td></tr>
<tr><td><code>|</code></td><td>bitwise or</td></tr>
</table>

<p>
The <em>bitwise negation operator</em> changes each 1 to 0 and 0 to 1.
</p>

<pre class="compact">
Console.WriteLine(~ 7); // prints -8
Console.WriteLine(~ -8); // prints 7
</pre>

<p>
The operator reverts all bits of a number 7. One of the bits also determines,
whether the number is negative or not. If we negate all the bits one more
time, we get number 7 again.
</p>

<p>
The <em>bitwise and operator</em> performs bit-by-bit comparison between
two numbers. The result for a bit position is 1 only if both corresponding
bits in the operands are 1.
</p>

<pre class="compact">
      00110
   &amp;  00011
   =  00010
</pre>

<p>
The first number is a binary notation of 6, the second is 3,
and the result is 2.
</p>

<pre class="compact">
Console.WriteLine(6 &amp; 3); // prints 2
Console.WriteLine(3 &amp; 6); // prints 2
</pre>

<p>
The <em>bitwise or operator</em> performs bit-by-bit comparison
between two numbers. The result for a bit position is 1 if either
of the corresponding bits in the operands is 1.
</p>

<pre class="compact">
     00110
   | 00011
   = 00111
</pre>

<p>
The result is <code>00110</code> or decimal 7.
</p>

<pre class="compact">
Console.WriteLine(6 | 3); // prints 7
Console.WriteLine(3 | 6); // prints 7
</pre>

<p>
The <em>bitwise exclusive or operator</em> performs bit-by-bit
comparison between two numbers.
The result for a bit position is 1 if one or the other (but not both)
of the corresponding bits in the operands is 1.
</p>

<pre class="compact">
      00110
   ^  00011
   =  00101
</pre>

<p>
The result is <code>00101</code> or decimal 5.
</p>

<pre class="compact">
Console.WriteLine(6 ^ 3); // prints 5
Console.WriteLine(3 ^ 6); // prints 5
</pre>


<h2>C# compound assignment operators</h2>

<p>
The compound assignment operators consist of two operators.
They are shorthand operators.
</p>

<pre class="compact">
a = a + 3;
a += 3;
</pre>

<p>
The <code>+=</code> compound operator is one of these shorthand operators.
The above two expressions are equal. Value 3 is added to the a variable.
</p>

<p>
Other compound operators are:
</p>

<pre class="compact">
<code>-=   *=   /=   %=   &amp;=   |=   &lt;&lt;=   &gt;&gt;=</code>
</pre>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
int a = 1;
a = a + 1;

Console.WriteLine(a);

a += 5;
Console.WriteLine(a);

a *= 3;
Console.WriteLine(a);
</pre>

<p>
In the example, we use two compound operators.
</p>

<pre class="explanation">
int a = 1;
a = a + 1;
</pre>

<p>
The <code>a</code> variable is initiated to one. 1 is added to the variable
using the non-shorthand notation.
</p>

<pre class="explanation">
a += 5;
</pre>

<p>
Using a <code>+=</code> compound operator, we add 5 to the
<code>a</code> variable. The statement is equal to <code>a = a + 5;</code>.
</p>

<pre class="explanation">
a *= 3;
</pre>

<p>
Using the <code>*=</code> operator, the <code>a</code> is multiplied by 3.
The statement is equal to <code>a = a * 3;</code>.
</p>

<pre class="compact">
$ dotnet run
2
7
21
</pre>




<h2>C# new operator</h2>

<p>
The <code>new</code> operator is used to create objects and invoke constructors.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
var b = new Being();
Console.WriteLine(b);

var vals = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine(string.Join(" ", vals));

class Being
{
    public Being()
    {
        Console.WriteLine("Being created");
    }
}
</pre>

<p>
In the example, we create a new custom object and a array of integers
utilizing the <code>new</code> operator.
</p>

<pre class="explanation">
public Being()
{
    Console.WriteLine("Being created");
}
</pre>

<p>
This is a constructor. It is called at the time of the object creation.
</p>

<pre class="compact">
$ dotnet run
Being created
Being
1 2 3 4 5
</pre>


<h2>C# access operator</h2>

<p>
The access operator <code>[]</code> is used with
arrays, indexers, and attributes.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
var vals = new int[] { 2, 4, 6, 8, 10 };
Console.WriteLine(vals[0]);

var domains = new Dictionary<string, string>()
{
    { "de", "Germany" },
    { "sk", "Slovakia" },
    { "ru", "Russia" }
};

Console.WriteLine(domains["de"]);

oldMethod();

[Obsolete("Don't use OldMethod, use NewMethod instead", false)]
void oldMethod()
{
    Console.WriteLine("oldMethod()");
}

void newMethod()
{
    Console.WriteLine("newMethod()");
}
</pre>

<p>
In the example, we use the <code>[]</code> operator to get an element of an
array, value of a dictionary pair, and activate a built-in attribute.
</p>

<pre class="explanation">
var vals = new int[] { 2, 4, 6, 8, 10 };
Console.WriteLine(vals[0]);
</pre>

<p>
We define an array of integers. We get the first element with <code>vals[0]</code>.
</p>

<pre class="explanation">
var domains = new Dictionary&lt;string, string&gt;()
{
    { "de", "Germany" },
    { "sk", "Slovakia" },
    { "ru", "Russia" }
};

Console.WriteLine(domains["de"]);
</pre>

<p>
A dictionary is created. With <code>domains["de"]</code>, we get the value of
the pair that has the <code>"de"</code> key.
</p>

<pre class="explanation">
[Obsolete("Don't use OldMethod, use NewMethod instead", false)]
public static void oldMethod()
{
    Console.WriteLine("oldMethod()");
}
</pre>

<p>
We active the built-in <code>Obsolete</code> attribute. The attribute
issues a warning.
</p>

<p>
When we run the program, it produces the warning: 
<code>warning CS0618: 'oldMethod()' is obsolete: 'Don't use OldMethod, use NewMethod instead'</code>.
</p>


<h2>C# index from end operator ^</h2>

<p>
The index from end operator ^ indicates the element position from the end of a
sequence. For instance, <code>^1</code> points to the last element of a sequence
and <code>^n</code> points to the element with offset <code>length - n</code>.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
int[] vals = { 1, 2, 3, 4, 5 };

Console.WriteLine(vals[^1]);
Console.WriteLine(vals[^2]);

var word = "gray falcon";

Console.WriteLine(word[^1]);
</pre>

<p>
In the example, we apply the operator on an array and a string.
</p>

<pre class="explanation">
int[] vals = { 1, 2, 3, 4, 5 };

Console.WriteLine(vals[^1]);
Console.WriteLine(vals[^2]);
</pre>

<p>
We print the last and the last but one element of the array.
</p>

<pre class="explanation">
var word = "gray falcon";

Console.WriteLine(word[^1]);
</pre>

<p>
We print the last letter of the word.
</p>

<pre class="compact">
$ dotnet run
5
4
n
</pre>


<h2>C# range operator ..</h2>

<p>
The <code>..</code> operator specifies the start and end of a range of indices
as its operands. The left-hand operand is an inclusive start of a range. The
right-hand operand is an exclusive end of a range.
</p>

<pre class="compact">
x.. is equivalent to x..^0
..y is equivalent to 0..y
.. is equivalent to 0..^0
</pre>

<p>
Operands of the <code>..</code> operator can be omitted to get an open-ended
range.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
int[] vals = { 1, 2, 3, 4, 5, 6, 7 };

var slice1 = vals[1..4];
Console.WriteLine("[{0}]", string.Join(", ", slice1));

var slice2 = vals[..^0];
Console.WriteLine("[{0}]", string.Join(", ", slice2));
</pre>

<p>
In the example, we use the <code>..</code> operator to get array slices.
</p>

<pre class="explanation">
var range1 = vals[1..4];
Console.WriteLine("[{0}]", string.Join(", ", range1));
</pre>

<p>
We create an array slice from index 1 till index 4; the last index 4
is not included.
</p>

<pre class="explanation">
var slice2 = vals[..^0];
Console.WriteLine("[{0}]", string.Join(", ", slice2));
</pre>

<p>
Here we esentially create a copy of the array.
</p>

<pre class="compact">
$ dotnet run
[2, 3, 4]
[1, 2, 3, 4, 5, 6, 7]
</pre>


<h2>C# type information</h2>

<p>
Now we concern ourselves with operators that work with types.
</p>

<p>
The <code>sizeof</code> operator is used to obtain the size
in bytes for a value type. The <code>typeof</code> is
used to obtain the <code>System.Type</code> object for a type.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
Console.WriteLine(sizeof(int));
Console.WriteLine(sizeof(float));
Console.WriteLine(sizeof(Int32));

Console.WriteLine(typeof(int));
Console.WriteLine(typeof(float));
</pre>

<p>
We use the <code>sizeof</code> and <code>typeof</code> operators.
</p>

<pre class="compact">
$ dotnet run
4
4
4
System.Int32
System.Single
</pre>

<p>
We can see that the <code>int</code> type is an alias for <code>System.Int32</code>
and the <code>float</code> is an alias for the <code>System.Single</code> type.
</p>

<p>
The <code>is</code> operator checks if an object is compatible with a given
type.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
Base _base = new Base();
Derived derived = new Derived();

Console.WriteLine(_base is Base);
Console.WriteLine(_base is Object);
Console.WriteLine(derived is Base);
Console.WriteLine(_base is Derived);

class Base { }
class Derived : Base { }
</pre>

<p>
We create two objects from user defined types.
</p>

<pre class="explanation">
class Base {}
class Derived : Base {}
</pre>

<p>
We have a <code>Base</code> and a <code>Derived</code> class.
The <code>Derived</code> class inherits from the <code>Base</code> class.
</p>

<pre class="explanation">
Console.WriteLine(_base is Base);
Console.WriteLine(_base is Object);
</pre>

<p>
<code>Base</code> equals <code>Base</code> and so the first line
prints True. The <code>Base</code> is also compatible with <code>Object</code>
type. This is because each class inherits from the mother of all classes —
the <code>Object</code> class.
</p>

<pre class="explanation">
Console.WriteLine(derived is Base);
Console.WriteLine(_base is Derived);
</pre>

<p>
The derived object is compatible with the <code>Base</code> class
because it explicitly inherits from the <code>Base</code> class. On
the other hand, the <code>_base</code> object has nothing to do with
the <code>Derived</code> class.
</p>

<pre class="compact">
$ dotnet run
True
True
True
False
</pre>


<p>
The <code>as</code> operator is used to perform conversions between compatible
reference types. When the conversion is not possible, the operator returns null.
Unlike the cast operation which raises an exception.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
object[] objects = new object[6];
objects[0] = new Base();
objects[1] = new Derived();
objects[2] = "ZetCode";
objects[3] = 12;
objects[4] = 1.4;
objects[5] = null;

for (int i = 0; i &lt; objects.Length; i++)
{
    string s = objects[i] as string;
    Console.Write("{0}:", i);

    if (s != null)
    {
        Console.WriteLine(s);
    }
    else
    {
        Console.WriteLine("not a string");
    }
}

class Base { }
class Derived : Base { }
</pre>

<p>
In the above example, we use the <code>as</code> operator to
perform casting.
</p>

<pre class="explanation">
string s = objects[i] as string;
</pre>

<p>
We try to cast various types to the string type. But only
once the casting is valid.
</p>

<pre class="compact">
$ dotnet run
0:not a string
1:not a string
2:ZetCode
3:not a string
4:not a string
5:not a string
</pre>


<h2>C# operator precedence</h2>

<p>
The <em>operator precedence</em> tells us which operators are evaluated first.
The precedence level is necessary to avoid ambiguity in expressions.
</p>

<p>
What is the outcome of the following expression, 28 or 40?
</p>

<pre class="compact">
3 + 5 * 5
</pre>

<p>
Like in mathematics, the multiplication operator has a higher
precedence than addition operator. So the outcome is 28.
</p>

<pre class="compact">
(3 + 5) * 5
</pre>

<p>
To change the order of evaluation, we can use parentheses.
Expressions inside parentheses are always evaluated first.
</p>

<p>
The following table shows common C# operators ordered by
precedence (highest precedence first):
</p>

<table>
  <tr>
    <th>Operator(s)</th>
    <th>Category</th>
    <th>Associativity</th>
  </tr>
  <tr>
    <td>Primary</td>
    <td><code>x.y  x?.y, x?[y] f(x)  a[x]  x++  x--  new  typeof  default  checked  unchecked</code></td>
    <td>Left</td>
  </tr>
  <tr>
    <td>Unary</td>
    <td><code>+  -  !  ~  ++x  --x  (T)x</code></td>
    <td>Left</td>
  </tr>
  <tr>
    <td>Multiplicative</td>
    <td><code>* / %</code></td>
    <td>Left</td>
  </tr>
  <tr>
    <td>Additive</td>
    <td><code>+ -</code></td>
    <td>Left</td>
  </tr>
  <tr>
    <td>Shift</td>
    <td><code>&lt;&lt; &gt;&gt;</code></td>
    <td>Left</td>
  </tr>
  <tr>
    <td>Equality</td>
    <td><code>== !=</code></td>
    <td>Right</td>
  </tr>
  <tr>
    <td>Logical AND</td>
    <td><code>&amp;</code></td>
    <td>Left</td>
  </tr>
  <tr>
    <td>Logical XOR</td>
    <td><code>^</code></td>
    <td>Left</td>
  </tr>
  <tr>
    <td>Logical OR</td>
    <td><code>|</code></td>
    <td>Left</td>
  </tr>
  <tr>
    <td>Conditional AND</td>
    <td><code>&amp;&amp;</code></td>
    <td>Left</td>
  </tr>
  <tr>
    <td>Conditional OR</td>
    <td><code>||</code></td>
    <td>Left</td>
  </tr>
  <tr>
    <td>Null Coalescing</td>
    <td><code>??</code></td>
    <td>Left</td>
  </tr>
  <tr>
    <td>Ternary</td>
    <td><code>?:</code></td>
    <td>Right</td>
  </tr>
  <tr>
    <td>Assignment</td>
    <td><code>=  *=  /=  %=  +=  -=  &lt;&lt;=  >>=  &amp;=  ^=  |=  ??=  =></code></td>
    <td>Right</td>
  </tr>
</table>

<p>
Operators on the same row of the table have the same precedence.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
Console.WriteLine(3 + 5 * 5);
Console.WriteLine((3 + 5) * 5);

Console.WriteLine(! true | true);
Console.WriteLine(! (true | true));
</pre>

<p>
In this code example, we show a few expressions. The outcome of each expression
is dependent on the precedence level.
</p>

<pre class="explanation">
Console.WriteLine(3 + 5 * 5);
</pre>

<p>
This line prints 28. The multiplication operator has a higher precedence
than addition. First, the product of <code>5*5</code> is calculated,
then 3 is added.
</p>

<pre class="explanation">
Console.WriteLine(! true | true);
</pre>

<p>
In this case, the negation operator has a higher precedence. First,
the first true value is negated to false, then the <code>|</code> operator
combines false and true, which gives true in the end.
</p>

<pre class="compact">
$ dotnet run
28
40
True
False
</pre>


<h2>C# associativity rule</h2>

<p>
Sometimes the precedence is not satisfactory to determine the outcome
of an expression. There is another rule called
<em>associativity</em>. The associativity of operators determines
the order of evaluation of operators with the <em>same</em>
precedence level.
</p>

<pre class="compact">
9 / 3 * 3
</pre>

<p>
What is the outcome of this expression, 9 or 1? The multiplication,
deletion and the modulo operator are left to right associated.
So the expression is evaluated this way: <code>(9 / 3) * 3</code>
and the result is 9.
</p>

<p>
Arithmetic, boolean, relational, and bitwise operators are all left
to right associated.
</p>

<p>
On the other hand, the assignment operator is right associated.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
int a, b, c, d;
a = b = c = d = 0;

Console.WriteLine("{0} {1} {2} {3}", a, b, c, d);

int j = 0;
j *= 3 + 1;

Console.WriteLine(j);
</pre>

<p>
In the example, we have two cases where the associativity rule
determines the expression.
</p>

<pre class="explanation">
int a, b, c, d;
a = b = c = d = 0;
</pre>

<p>
The assignment operator is right to left associated.
If the associativity was left to right, the previous expression
would not be possible.
</p>

<pre class="explanation">
int j = 0;
j *= 3 + 1;
</pre>

<p>
The compound assignment operators are right to left associated.
We might expect the result to be 1. But the actual result is 0.
Because of the associativity. The expression on the right is
evaluated first and than the compound assignment operator is applied.
</p>

<pre class="compact">
$ dotnet run
0 0 0 0
0
</pre>


<h2>C# null-conditional operator</h2>

<p>
A <em>null-conditional operator</em> applies a member access, <code>?.</code>,
or element access, <code> ?[]</code>, operation to its operand only if that
operand evaluates to non-null. If the operand evaluates to <code>null</code>,
the result of applying the operator is null.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
var users = new List&lt;User&gt;() { new User("John Doe", "gardener"), new User(null, null),
        new User("Lucia Newton", "teacher") };

users.ForEach(user =&gt; Console.WriteLine(user.Name?.ToUpper()));

record User(string? Name, string? Occupation);
</pre>

<p>
In the example, we have a <code>User</code> class with two members: <code>Name</code>
and <code>Occupation</code>. We access the <code>name</code> member of the
objects with the help of the <code>?.</code> operator.
</p>

<pre class="explanation">
var users = new List&lt;User&gt;() { new User("John Doe", "gardener"), new User(null, null),
        new User("Lucia Newton", "teacher") };
</pre>

<p>
We have a list of users. One of them is initialized with null values.
</p>

<pre class="explanation">
users.ForEach(user =&gt; Console.WriteLine(user.Name?.ToUpper()));
</pre>

<p>
We use the <code>?.</code> to access the <code>Name</code> member and call
the <code>ToUpper</code> method. The <code>?.</code> prevents the
<code>System.NullReferenceException</code> by not calling the
<code>ToUpper</code> on the <code>null</code> value.
</p>

<pre class="compact">
$ dotnet run
JOHN DOE

LUCIA NEWTON
</pre>


<p>
In the following example, we use the <code>?[]</code> operator. The operator 
allows to place <code>null</code> values into a collection.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
int?[] vals = { 1, 2, 3, null, 4, 5 };

int i = 0;

while (i &lt; vals.Length)
{
    Console.WriteLine(vals[i]?.GetType());
    i++;
}
</pre>

<p>
In this example, we have a <code>null</code> value in an array. 
We prevent the <code>System.NullReferenceException</code> by applying 
the <code>?.</code> operator on the array elements.
</p>


<h2>C# null-coalescing operator</h2>

<p>
The null-coalescing operator <code>??</code> is used to define a default value
for a <code>nullable</code> type. It returns the left-hand operand if it is not
null; otherwise it returns the right operand. When we work with databases, we
often deal with absent values. These values come as nulls to the program. This
operator is a convenient way to deal with such situations.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
int? x = null;
int? y = null;

int z = x ?? y ?? -1;

Console.WriteLine(z);
</pre>

<p>
An example program for null-coalescing operator.
</p>

<pre class="explanation">
int? x = null;
int? y = null;
</pre>

<p>
Two nullable <code>int</code> types are initiated to <code>null</code>.
The <code>int?</code> is a shorthand for <code>Nullable&lt;int&gt;</code>.
It allows to have null values assigned to <code>int</code> types.
</p>

<pre class="explanation">
int z = x ?? y ?? -1;
</pre>

<p>
We want to assign a value to <code>z</code> variable. But it must not
be <code>null</code>. This is our requirement. We can easily use the
null-coalescing operator for that. In case both <code>x</code> and <code>y</code>
variables are null, we assign -1 to <code>z</code>.
</p>

<pre class="compact">
$ dotnet run
-1
</pre>


<h2>C# null-coalescing assignment operator</h2>

<p>
The null-coalescing assignment operator <code>??=</code> assigns the value of
its right-hand operand to its left-hand operand only if the left-hand operand
evaluates to <code>null</code>. The <code>??=</code> operator does not evaluate
its right-hand operand if the left-hand operand evaluates to non-null. It is
available in C# 8.0 and later.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
List&lt;int&gt; vals = null;

vals ??= new List&lt;int&gt;() {1, 2, 3, 4, 5, 6};
vals.Add(7);
vals.Add(8);
vals.Add(9);

Console.WriteLine(string.Join(", ", vals));

vals ??= new List&lt;int&gt;() {1, 2, 3, 4, 5, 6};

Console.WriteLine(string.Join(", ", vals));
</pre>

<p>
In the example, we use the null-coalescing assignment operator on a list 
of integer values.
</p>

<pre class="explanation">
List&lt;int&gt; vals = null;
</pre>

<p>
First, the list is assigned to <code>null</code>.
</p>

<pre class="explanation">
vals ??= new List&lt;int&gt;() {1, 2, 3, 4, 5, 6};
</pre>

<p>
We use the <code>??=</code> to assign a new list object to the variable.
Since it is <code>null</code>, the list is assigned.
</p>

<pre class="explanation">
vals.Add(7);
vals.Add(8);
vals.Add(9);

Console.WriteLine(string.Join(", ", vals));
</pre>

<p>
We add some values to the list and print its contents.
</p>

<pre class="explanation">
vals ??= new List&lt;int&gt;() {1, 2, 3, 4, 5, 6};
</pre>

<p>
We try to assign a new list object to the variable. Since the variable 
is not <code>null</code> anymore, the list is not assigned.
</p>

<pre class="compact">
$ dotnet run
1, 2, 3, 4, 5, 6, 7, 8, 9
1, 2, 3, 4, 5, 6, 7, 8, 9
</pre>


<h2>C# ternary operator</h2>

<p>
The ternary operator <code>?:</code> is a conditional operator. It is a
convenient operator for cases where we want to pick up one of two values,
depending on the conditional expression.
</p>

<pre class="compact">
cond-exp ? exp1 : exp2
</pre>

<p>
If cond-exp is true, exp1 is evaluated and the result is returned. If the
cond-exp is false, exp2 is evaluated and its result is returned.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
int age = 31;

bool adult = age &gt;= 18 ? true : false;

Console.WriteLine("Adult: {0}", adult);
</pre>

<p>
In most countries the adulthood is based on your age. You are adult if you are
older than a certain age. This is a situation for a ternary operator.
</p>

<pre class="explanation">
bool adult = age &gt;= 18 ? true : false;
</pre>

<p>
First the expression on the right side of the assignment operator is evaluated.
The first phase of the ternary operator is the condition expression evaluation.
So if the age is greater or equal to 18, the value following the <code>?</code>
character is returned. If not, the value following the <code>:</code> character
is returned. The returned value is then assigned to the adult variable.
</p>

<pre class="compact">
$ dotnet run
Adult: True
</pre>

<p>
A 31 years old person is adult.
</p>


<h2>C# Lambda operator</h2>

<p>
The <code>=&gt;</code> token is called the lambda operator. It is an operator
taken from functional languages. This operator can make the code shorter and
cleaner. On the other hand, understanding the syntax may be tricky. Especially
if a programmer never used a functional language before.
</p>

<p>
Wherever we can use a delegate, we also can use a lambda expression. A
definition for a lambda expression is: a lambda expression is an anonymous
function that can contain expressions and statements. On the left side we have a
group of data and on the right side an expression or a block of statements.
These statements are applied on each item of the data.
</p>

<p>
In lambda expressions we do not have a return keyword. The last statement is
automatically returned. And we do not need to specify types for our parameters.
The compiler will guess the correct parameter type. This is called type
inference.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
var list = new List&lt;int&gt;() { 3, 2, 1, 8, 6, 4, 7, 9, 5 };

var subList = list.FindAll(val =&gt; val &gt; 3);

foreach (int i in subList)
{
    Console.WriteLine(i);
}
</pre>

<p>
We have a list of integer numbers. We print all numbers that are
greater than 3.
</p>

<pre class="explanation">
var list = new List&lt;int&gt;() { 3, 2, 1, 8, 6, 4, 7, 9, 5 };
</pre>

<p>
We have a generic list of integers.
</p>

<pre class="explanation">
var subList = list.FindAll(val =&gt; val &gt; 3);
</pre>

<p>
Here we use the lambda operator. The <code>FindAll</code> method takes a
predicate as a parameter. A predicate is a special kind of a delegate that
returns a boolean value. The predicate is applied for all items of the list. The
<code>val</code> is an input parameter specified without a type. We could
explicitly specify the type but it is not necessary. 
</p>

<p>
The compiler will expect an <code>int</code> type. The <code>val</code> is a
current input value from the list. It is compared if it is greater than 3 and a
boolean true or false is returned. Finally, the <code>FindAll</code> will
return all values that met the condition. They are assigned to the sublist
collection.
</p>

<pre class="explanation">
foreach (int i in subList)
{
    Console.WriteLine(i);
}
</pre>

<p>
The items of the sublist collection are printed to the terminal.
</p>

<pre class="compact">
$ dotnet run
8
6
4
7
9
5
</pre>

<p>
Values from the list of integers that are greater than 3.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
var nums = new List&lt;int&gt;() { 3, 2, 1, 8, 6, 4, 7, 9, 5 };

var nums2 = nums.FindAll( delegate(int i) {
        return i &gt; 3;
    }
);

foreach (int i in nums2)
{
    Console.WriteLine(i);
}
</pre>

<p>
This is the same example. We use a anonymous delegate instead
of a lambda expression.
</p>


<h2>C# calculating prime numbers</h2>

<p>
We are going to calculate prime numbers.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
int[] nums = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 
    14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28 };

Console.Write("Prime numbers: ");

foreach (int num in nums)
{
    if (num == 1) continue;

    if (num == 2 || num == 3)
    {
        Console.Write(num + " ");
        continue;
    }

    int i = (int) Math.Sqrt(num);
    bool isPrime = true;

    while (i &gt; 1)
    {
        if (num % i == 0)
        {
            isPrime = false;
        }
        i--;
    }

    if (isPrime)
    {
        Console.Write(num + " ");
    }
}

Console.Write('\n');
</pre>

<p>
In the above example, we deal with many various operators. A prime number (or a
prime) is a natural number that has exactly two distinct natural number
divisors: 1 and itself. We pick up a number and divide it by numbers, from 1 up
to the picked up number. Actually, we do not have to try all smaller numbers; we
can divide by numbers up to the square root of the chosen number. The formula
will work. We use the remainder division operator.
</p>

<pre class="explanation">
int[] nums = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 
    14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28 };
</pre>

<p>
We calculate primes from these numbers.
</p>

<pre class="explanation">
if (num == 1) continue;
</pre>

<p>
By definition, 1 is not a prime
</p>

<pre class="explanation">
if (num == 2 || num == 3)
{
    Console.Write(num + " ");
    continue;
}
</pre>

<p>
We skip the calculations for 2 and 3: they are primes. Note the
usage of the equality and conditional or operators. The <code>==</code>
has a higher precedence than the <code>||</code> operator.
So we do not need to use parentheses.
</p>

<pre class="explanation">
int i = (int) Math.Sqrt(num);
</pre>

<p>
We are OK if we only try numbers smaller than the square root of a number in
question. It was mathematically proven that it is sufficient to take into 
account values up to the square root of the number in question.
</p>

<pre class="explanation">
while (i &gt; 1)
{
    ...
    i--;
}
</pre>

<p>
This is a while loop. The <code>i</code> is the calculated square root of the
number. We use the decrement operator to decrease the i by one each loop cycle.
When the i is smaller than 1, we terminate the loop. For example, we have number
9. The square root of 9 is 3. We divide the 9 number by 3 and 2. 
</p>

<pre class="explanation">
if (num % i == 0)
{
    isPrime = false;
}
</pre>

<p>
This is the core of the algorithm. If the remainder division operator returns 0
for any of the i values then the number in question is not a prime.
</p>

<h2>Source</h2>

<p>
<a href="https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/">C# operators and expressions</a>
</p>

<p>
In this article we covered C# operators.
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

