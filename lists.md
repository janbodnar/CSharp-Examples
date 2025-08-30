
<!DOCTYPE html>
<html lang="en">
<head>
<title>C# List - working with a List collection in C#</title>
<link rel="stylesheet" href="/cfg/style.css" type="text/css">
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="keywords" content=<meta name="keywords" content="C# List tutorial,
C# collections, List in C#, .NET generics, List methods in C#, sort List in C#,
search List in C#, C# data structures, learn C# programming, C# List vs array">
<meta name="description" content="Learn how to work with the List collection in
C#. This tutorial covers List manipulation, indexing, sorting, searching, and
common operations for handling data efficiently using .NET collections.">
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
<h1>C# List</h1>

<p class="last_mod">
last modified May 14, 2025
</p>
 
<p>
This article provides a comprehensive guide on working with the
<code>List</code> collection in C#. Learn how to efficiently store, manage, and
manipulate dynamic lists in your applications.
</p>

<h2>C# List</h2>

<p>
The <code>List</code> class in C# represents a strongly typed, resizable
collection of objects that can be accessed via index. It offers powerful methods
for searching, sorting, filtering, and modifying list elements dynamically,
making it an essential tool for handling structured data.
</p>


<p>
Key Features of the List class:
</p>

<ul>
    <li><strong>Dynamic Sizing:</strong> Lists automatically expand when new
    elements are added and contract when elements are removed.</li>
    <li><strong>Index-Based Access:</strong> Elements can be accessed directly
    using zero-based indexing.</li>
    <li><strong>Generic Type Support:</strong> Lists are strongly typed using
    generics, ensuring type safety.</li>
    <li><strong>Versatile Methods:</strong> Built-in methods simplify common
    operations such as sorting, searching, filtering, and modifying
    elements.</li>
    <li><strong>Efficient Performance:</strong> Optimized for fast insertion,
    deletion, and iteration compared to arrays in certain scenarios.</li>
</ul>

<h3>Common Methods and Operations</h3>

<p>
The List class provides a variety of methods for manipulating lists. 
Here are some of the most commonly used methods:
</p>

<table>
    <thead>
        <tr>
            <th>Method</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>Add(T item)</code></td>
            <td>Adds an element to the end of the list.</td>
        </tr>
        <tr>
            <td><code>Insert(int index, T item)</code></td>
            <td>Inserts an element at a specified index.</td>
        </tr>
        <tr>
            <td><code>Remove(T item)</code></td>
            <td>Removes the first occurrence of a specified item.</td>
        </tr>
        <tr>
            <td><code>RemoveAt(int index)</code></td>
            <td>Removes an element at a specified index.</td>
        </tr>
        <tr>
            <td><code>Contains(T item)</code></td>
            <td>Checks if an element exists in the list.</td>
        </tr>
        <tr>
            <td><code>IndexOf(T item)</code></td>
            <td>Gets the index of the first occurrence of a specified item.</td>
        </tr>
        <tr>
            <td><code>Sort</code></td>
            <td>Sorts the list in ascending order.</td>
        </tr>
        <tr>
            <td><code>Reverse</code></td>
            <td>Reverses the order of the list.</td>
        </tr>
        <tr>
            <td><code>Clear</code></td>
            <td>Removes all elements from the list.</td>
        </tr>
        <tr>
            <td><code>Count</code></td>
            <td>Returns the number of elements in the list.</td>
        </tr>
    </tbody>
</table>

<p>
These methods make the <code>List</code> class a versatile data structure for
handling dynamic collections in C#. Whether you need to add, remove, or reorder
elements, these built-in functionalities provide an efficient way to manage
lists without manual memory allocation or complex operations. 
</p>

<h2>C# List initializer</h2>

<p>
C# lists can be initialized with literal notation. The elements
are added on the right side of the assignment inside <code>{}</code>
brackets.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
var words = new List&lt;string&gt; { "forest", "oak", "river", "falcon" };
Console.WriteLine(string.Join(", ", words));
</pre>

<p>
In the example, we create a list of strings with list initializer.
</p>

<pre class="explanation">
var words = new List&lt;string&gt;{"forest", "oak", "river", "falcon"};
</pre>

<p>
A new list is created. Between the angle brackets (<code>&lt;&gt;</code>),
we specify the data type of the list elements.
</p>

<pre class="explanation">
Console.WriteLine(string.Join(", ", words));
</pre>

<p>
To get a quick look at the contents of the list, we join all the values into
a string, separated by comma.
</p>

<pre class="compact">
$ dotnet run
forest, oak, river, falcon
</pre>


<h2>C# List collection expression</h2>

<p>
.NET 8 introduced a terse syntax to create and initialize a list.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
List&lt;string&gt; words = ["forest", "oak", "river", "falcon"];
Console.WriteLine(string.Join(", ", words));
</pre>

<p>
The elements of the list are placed inside a pair of square brackets 
(<code>[]</code>). This syntax is shared by many programming languages. 
</p>


<h2>C# List count elements</h2>

<p>
With the <code>Count</code> property, we get the number of elements in the list.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
List&lt;int&gt; vals = [0, 1, 2, 3, 4, 5];
Console.WriteLine($"There are {vals.Count} elements in the list");
</pre>

<p>
The example counts the number of elements in the list.
</p>

<pre class="explanation">
Console.WriteLine($"There are {vals.Count} elements in the list");
</pre>

<p>
Here we print the number of elements in the List.
</p>

<pre class="compact">
$ dotnet run
There are 6 elements in the list
</pre>


<h2>C# List access elements</h2>

<p>
Elements of a list can be accessed using the index notation <code>[]</code>.
The index is zero-based.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
List&lt;int&gt; vals = [0, 1, 2, 3, 4, 5];

Console.WriteLine(vals[0]);
Console.WriteLine(vals[1]);

Console.WriteLine(vals.Count - 1);

Console.WriteLine(vals[^1]);
Console.WriteLine(vals[^2]);
</pre>

<p>
The example prints the first, second, and the last element of the list.
</p>

<pre class="explanation">
Console.WriteLine(vals.Count - 1);
</pre>

<p>
To get the last element of the list, we count the number of elements and divide
one.
</p>

<pre class="explanation">
Console.WriteLine(vals[^1]);
Console.WriteLine(vals[^2]);
</pre>

<p>
With the <code>^</code> operator, we can access elements from the end of the
list.
</p>

<pre class="compact">
$ dotnet run
0
1
5
5
4
</pre>



<h2>C# List add elements</h2>

<p>
The <code>Add</code> method adds an element at the end of the list. The
<code>AddRange</code> methods adds the elements of the specified collection to
the end of the list.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
List&lt;string&gt; words = ["forest", "oak", "river", "falcon"];

words.Add("sky");
words.Add("ocean");

string[] words2 = ["owl", "hawk"];
words.AddRange(words2);

Console.WriteLine(string.Join(',', words));
</pre>

<p>
The example creates two lists and adds new elements to it.
</p>

<pre class="explanation">
words.Add("sky");
words.Add("ocean");
</pre>

<p>
Two elements are added to the list with <code>Add</code>.
</p>

<pre class="explanation">
string[] words2 = ["owl", "hawk"];
words.AddRange(words2);
</pre>

<p>
With <code>AddRange</code> method, we add another collection to the list.
</p>

<pre class="compact">
$ dotnet run
forest,oak,river,falcon,sky,ocean,owl,hawk
</pre>



<h2>C# List insert elements</h2>

<p>
The <code>Insert</code> method inserts an element into the list at the specified
index. The <code>InsertRange</code> inserts the elements of a collection into
the list at the specified index.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
List&lt;string&gt; words = ["forest", "oak", "river", "falcon"];

words.Insert(0, "sky");
words.Insert(words.Count, "cloud");

List&lt;string&gt; words2 =["water", "wave"];
words.InsertRange(2, words2);

Console.WriteLine(string.Join(", ", words));
</pre>

<p>
The example creates a new list of words and inserts new elements to it.
</p>

<pre class="compact">
$ dotnet run
sky, forest, water, wave, oak, river, falcon, cloud
</pre>



<h2>C# List Contains</h2>

<p>
The <code>Contains</code> method determines whether the element is in the list.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
List&lt;string&gt; words =  ["forest", "oak", "river", "falcon"];

if (words.Contains("oak"))
{
    Console.WriteLine("The list contains the oak word");
}
</pre>

<p>
In the example, we check if the <code>oak</code> word is in the list.
</p>


<h2>C# List removing elements</h2>

<p>
The <code>Remove</code>, <code>RemoveAt</code>, <code>RemoveAll</code>,
<code>RemoveRange</code>, and <code>Clear</code> methods can be used to remove
elements from a list.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
List&lt;int&gt; nums = [0, 1, 2, -3, 4, -5, 6, 7, -8, 9, 10];

nums.RemoveAll(e =&gt; e &lt; 0);
Console.WriteLine(string.Join(", ", nums));

nums.Remove(0);
nums.RemoveAt(nums.Count - 1);

Console.WriteLine(string.Join(", ", nums));

nums.RemoveRange(0, 3);

Console.WriteLine(string.Join(", ", nums));

nums.Clear();
Console.WriteLine("{0}", nums.Count);
</pre>

<p>
In the example, we remove elements from the list of integers.
</p>

<pre class="explanation">
nums.RemoveAll(e =&gt; e &lt; 0);
Console.WriteLine(string.Join(", ", nums));
</pre>

<p>
With <code>RemoveAll</code> method, we remove all elements that satisfy the
given predicate; in our case, we remove all negative values.
</p>

<pre class="explanation">
nums.Remove(0);
</pre>

<p>
The <code>Remove</code> method removes the first occurrence of the 0 value.
</p>

<pre class="explanation">
nums.RemoveAt(nums.Count - 1);
</pre>

<p>
With <code>RemoveAt</code>, we remove the element at the given index.
</p>

<pre class="explanation">
nums.RemoveRange(0, 3);
</pre>

<p>
The <code>RemoveRange</code> method removes the given range of values from the
list. The parameters are the zero-based starting index of the range of elements
to remove and the number of elements to remove.
</p>


<h2>C# List ToArray</h2>

<p>
The <code>ToArray</code> method copies the elements of a list into an array.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
List&lt;int&gt; nums = [1, 2, 3, 4];

Console.WriteLine(nums.GetType());

var nums2 = nums.ToArray();
Console.WriteLine(nums2.GetType());
</pre>

<p>
In the example, we create an array from a list. We print the type of both
containers with <code>GetType</code>.
</p>

<pre class="compact">
$ dotnet run
System.Collections.Generic.List`1[System.Int32]
System.Int32[]
</pre>


<h2>C# List ForEach</h2>

<p>
The <code>ForEach</code> method performs the specified action on each element
of a list.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
List&lt;string&gt; words = ["forest", "oak", "river", "falcon"];

words.ForEach(Console.WriteLine);
words.ForEach(word =&gt; Console.WriteLine(word.ToUpper()));
</pre>

<p>
We call the <code>ForEach</code> method twice on a list of words.
</p>

<pre class="explanation">
words.ForEach(Console.WriteLine);
</pre>

<p>
We print all elements of the list.
</p>

<pre class="explanation">
words.ForEach(word =&gt; Console.WriteLine(word.ToUpper()));
</pre>

<p>
Here we also print all elements of the list; the words are transformed to
uppercase.
</p>

<pre class="compact">
$ dotnet run
forest
oak
river
falcon
FOREST
OAK
RIVER
FALCON
</pre>




<h2>C# loop List</h2>

<p>
There are several ways to loop over a C# list.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
List&lt;int&gt; nums = [1, 2, 3, 4];

nums.ForEach(e =&gt; Console.WriteLine(e));

Console.WriteLine("********************");

foreach (int e in nums)
{

    Console.WriteLine(e);
}

Console.WriteLine("********************");

for (int i = 0; i &lt; nums.Count; i++)
{

    Console.WriteLine(nums[i]);
}
</pre>

<p>
The example shows three ways of looping over a list in C#.
</p>

<pre class="explanation">
nums.ForEach(e =&gt; Console.WriteLine(e));
</pre>

<p>
We loop over a list with <code>ForEach</code>.
</p>

<pre class="explanation">
foreach(int e in nums)
{
    Console.WriteLine(e);
}
</pre>

<p>
In this case, we use the <code>foreach</code> statement.
</p>

<pre class="explanation">
for (int i = 0; i &lt; nums.Count; i++)
{
    Console.WriteLine(nums[i]);
}
</pre>

<p>
Finally, this is the classic for loop.
</p>

<pre class="compact">
$ dotnet run
1
2
3
4
********************
1
2
3
4
********************
1
2
3
4
</pre>



<h2>C# sort, reverse List</h2>

<p>
The <code>Sort</code> method sorts the elements of a list, the
<code>Reverse</code> method reverses the elements of the list.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
List&lt;int&gt; nums = [2, 1, 5, 4, 3];

nums.Reverse();
Console.WriteLine(string.Join(',', nums));

nums.Sort();
Console.WriteLine(string.Join(',', nums));
</pre>

<p>
The example reverses the elements of the list of integers and then sorts them.
</p>

<pre class="compact">
$ dotnet run
3,4,5,1,2
1,2,3,4,5
</pre>


<h2>C# List FindAll</h2>

<p>
The <code>FindAll</code> method retrieves all the elements of a list that match
the conditions defined by the specified predicate. It returns a list containing
all the elements that match the conditions defined by the specified predicate,
if found; otherwise, an empty list.
</p>

<p>
A predicate is a method that returns a boolean value. To learn more about
predicates, visit the <a href="/csharp/predicate/">C# Predicate tutorial</a>.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
List&lt;int&gt; vals = [-1, -3, 0, 1, 3, 2, 9, -4];
List&lt;int&gt; filtered = vals.FindAll(e =&gt; e &gt; 0);

Console.WriteLine(string.Join(',', filtered));
</pre>

<p>
The example finds all positive elements.
</p>

<pre class="explanation">
List&lt;int&gt; filtered = vals.FindAll(e =&gt; e &gt; 0);
</pre>

<p>
The predicate is an expression that returns true for values greater than zero.
</p>

<pre class="compact">
$ dotnet run
1,3,2,9
</pre>

<p>
These are the positive values of the list.
</p>


<h2>C# List Find, FindLast, FindIndex, FindLastIndex</h2>

<p>
The <code>Find</code> method returns the first occurrence of the element that
matches the given predicate. The <code>FindLast</code> method  returns the last
occurrence of the element that matches the given predicate.
</p>

<p>
The <code>FindIndex</code> method returns the index of the first occurrence of
the element that matches the given predicate. The <code>FindLastIndex</code>
method returns the index of the last occurrence of the element that matches the
given predicate.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
List&lt;int&gt; nums = [6, -2, 1, 5, 4, 3, 2, 9, -1, 7];

var found = nums.Find(e =&gt; e &lt; 0);
Console.WriteLine(found);

var found2 = nums.FindIndex(e =&gt; e &lt; 0);
Console.WriteLine(found2);

var found3 = nums.FindLast(e =&gt; e &lt; 0);
Console.WriteLine(found3);

var found4 = nums.FindLastIndex(e =&gt; e &lt; 0);
Console.WriteLine(found4);
</pre>

<p>
The example uses all the mentioned methods to find elements and indexes.
</p>

<pre class="compact">
$ dotnet run
-2
1
-1
8
</pre>


<h2>C# List ConvertAll</h2>

<p>
The <code>ConvertAll</code> method converts the elements in the current List to
another type, and returns a list containing the converted elements.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
List&lt;string&gt; words = ["falcon", "owl", "sky", "hawk", "stork"];

List&lt;string&gt; uppedWords = words.ConvertAll(s =&gt; s.ToUpper());
List&lt;int&gt; lengths = words.ConvertAll(s =&gt; s.Length);

Console.WriteLine(string.Join(", ", uppedWords));
Console.WriteLine(string.Join(", ", lengths));
</pre>

<p>
In the example, we have a list of words. We convert the list to two other lists.
</p>

<pre class="explanation">
List&lt;string&gt; uppedWords = words.ConvertAll(s =&gt; s.ToUpper());
</pre>

<p>
Here we convert the list to a list containing words transformed into uppercase.
</p>

<pre class="explanation">
List&lt;int&gt; lengths = words.ConvertAll(s =&gt; s.Length);
</pre>

<p>
In the second case, the converted list contains integers that are the length of
the words in the original list.
</p>

<pre class="compact">
$ dotnet run
FALCON, OWL, SKY, HAWK, STORK
6, 3, 3, 4, 5
</pre>


<p>
In the second example, we have a separate <code>squareRoot</code> method, which
is applied on the list of integers.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
double squareRoot(int x)
{
    return Math.Sqrt(x);
}

List&lt;int&gt; vals = [1, 4, 9, 16, 25];

Converter&lt;int, double&gt; converter = squareRoot;
List&lt;double&gt; vals2 = vals.ConvertAll(converter);

Console.WriteLine(string.Join(", ", vals2));
</pre>

<p>
In the example, we create a new list by applying square root operation on the
list of integers.
</p>

<pre class="compact">
$ dotnet run
1, 2, 3, 4, 5
</pre>


<h2>C# List shuffle</h2>

<p>
The following example randomly rebuilds a list of integer values.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
List&lt;int&gt; vals = [1, 2, 3, 4, 5, 6, 7, 8];
vals.Shuffle();

var res = string.Join(" ", vals);
Console.WriteLine(res);

static class MyExtensions
{
    private static readonly Random rng = new();

    public static void Shuffle&lt;T&gt;(this IList&lt;T&gt; vals)
    {
        int n = vals.Count;

        while (n &gt; 1)
        {
            n--;
            int k = rng.Next(n + 1);

            (vals[n], vals[k]) = (vals[k], vals[n]);
        }
    }
}
</pre>

<p>
In the example, we create a <code>Shuffle</code> extension method. It shuffles 
the elements in-place.
</p>

<pre class="explanation">
public static void Shuffle&lt;T&gt;(this IList&lt;T&gt; vals)
{
    int n = vals.Count;

    while (n &gt; 1)
    {
        n--;
        int k = rng.Next(n + 1);

        (vals[n], vals[k]) = (vals[k], vals[n]);
    }
}
</pre>

<p>
This is an implementation of the Fisher-Yates shuffling algorithm.
</p>

<pre class="compact">
$ dotnet run
7 1 5 6 4 2 3 8
$ dotnet run
7 5 4 1 2 3 6 8
$ dotnet run
2 3 8 5 1 4 7 6
$ dotnet run
4 5 1 6 8 2 3 7
</pre>



<h2>C# List TrueForAll</h2>

<p>
The <code>TrueForAll</code> determines whether every element in the list
matches the conditions defined by the given predicate.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
List&lt;int&gt; nums = [1, 2, 3, 4, 5, 6, 7, 8];

var res1 = nums.TrueForAll(e =&gt; e % 2 == 0);
Console.WriteLine(res1);

var res2 = nums.TrueForAll(e =&gt; e &gt; 0);
Console.WriteLine(res2);
</pre>

<p>
In the example, we check if the elements in the list are all even and that they
are all positive.
</p>

<pre class="compact">
$ dotnet run
False
True
</pre>

<p>
Not all elements are even and all elements are positive.
</p>


<h2>LINQ</h2>

<p>
<dfn>Language-Integrated Query (LINQ)</dfn> is the name for a set of
technologies based on the integration of query capabilities directly into the C#
language.
</p>

<p>
Via LINQ, C# exposes plenty of methods for working with List data.
</p>


<h2>C# List aggregate calculations</h2>

<p>
LINQ has extension methods to calculate aggregate calculations, such as min,
max, or sum. 
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
List&lt;int&gt; vals = [-1, 2, 1, -3, 7, -9, 5, 9, -4, 8];

var n1 = vals.Count;
Console.WriteLine($"There are {n1} elements");

var n2 = vals.Count(e =&gt; e % 2 == 0);
Console.WriteLine($"There are {n2} even elements");

var sum = vals.Sum();
Console.WriteLine($"The sum of all values is: {sum}");

var s2 = vals.Sum(e =&gt; e &gt; 0 ? e : 0);
Console.WriteLine($"The sum of all positive values is: {s2}");

var avg = vals.Average();
Console.WriteLine($"The average of values is: {avg}");

var max = vals.Max();
Console.WriteLine($"The maximum value is: {max}");

var min = vals.Min();
Console.WriteLine($"The minimum value is: {min}");
</pre>

<p>
In the program, we use the Count, Sum, Average, Max, and Min methods. 
</p>

<pre class="compact">
$ dotnet run
There are 10 elements
There are 3 even elements
The sum of all values is: 15
The sum of all positive values is: 32
The average of values is: 1.5
The maximum value is: 9
The minimum value is: -9
</pre>


<h2>C# List ordering</h2>

<p>
To order data, we can use the <code>OrderBy</code> and <code>ThenBy</code>
extension methods. Note that the methods create a new modified list; the
original list is not changed.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
List&lt;User&gt; users =
[
    new ("John", "Doe", 1230),
    new ("Lucy", "Novak", 670),
    new ("Ben", "Walter", 2050),
    new ("Robin", "Brown", 2300),
    new ("Amy", "Doe", 1250),
    new ("Joe", "Draker", 1190),
    new ("Janet", "Doe", 980),
    new ("Albert", "Novak", 1930),
];

Console.WriteLine("sort ascending by last name and salary");

var sortedUsers = users.OrderBy(u =&gt; u.LastName).ThenBy(u =&gt; u.Salary);

foreach (var user in sortedUsers)
{
    Console.WriteLine(user);
}

Console.WriteLine("---------------------");

Console.WriteLine("sort descending by last name and salary");

var sortedUsers2 = users.OrderByDescending(u =&gt; u.LastName)
    .ThenByDescending(u =&gt; u.Salary);

foreach (var user in sortedUsers2)
{
    Console.WriteLine(user);
}

record User(string FirstName, string LastName, int Salary);
</pre>

<p>
We have a list of users. The users are sorted first by their last names, then by
their salaries.
</p>

<pre class="explanation">
var sortedUsers = users.OrderBy(u =&gt; u.LastName).ThenBy(u =&gt; u.Salary);
</pre>

<p>
We sort the users by their last names and then by their salaries in ascending
order. 
</p>

<pre class="explanation">
var sortedUsers2 = users.OrderByDescending(u =&gt; u.LastName)
    .ThenByDescending(u =&gt; u.Salary);
</pre>

<p>
Here, we sort the users by their last names and then by their salaries in
descending order. 
</p>

<pre class="compact">
$ dotnet run
sort ascending by last name and salary
User { FirstName = Robin, LastName = Brown, Salary = 2300 }
User { FirstName = Janet, LastName = Doe, Salary = 980 }
User { FirstName = John, LastName = Doe, Salary = 1230 }
User { FirstName = Amy, LastName = Doe, Salary = 1250 }
User { FirstName = Joe, LastName = Draker, Salary = 1190 }
User { FirstName = Lucy, LastName = Novak, Salary = 670 }
User { FirstName = Albert, LastName = Novak, Salary = 1930 }
User { FirstName = Ben, LastName = Walter, Salary = 2050 }
---------------------
sort descending by last name and salary
User { FirstName = Ben, LastName = Walter, Salary = 2050 }
User { FirstName = Albert, LastName = Novak, Salary = 1930 }
User { FirstName = Lucy, LastName = Novak, Salary = 670 }
User { FirstName = Joe, LastName = Draker, Salary = 1190 }
User { FirstName = Amy, LastName = Doe, Salary = 1250 }
User { FirstName = John, LastName = Doe, Salary = 1230 }
User { FirstName = Janet, LastName = Doe, Salary = 980 }
User { FirstName = Robin, LastName = Brown, Salary = 2300 }
</pre>


<h2>C# List remove duplicates with Distinct</h2>

<p>
The <code>Distinct</code> method removes duplicate elements from a list.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
List&lt;int&gt; nums = [1, 2, 2, 3, 4, 4, 5];

var unique = nums.Distinct().ToList();
Console.WriteLine(string.Join(", ", unique));
</pre>

<p>
This example removes duplicate elements from a list using the <code>Distinct</code>
method from LINQ. The resulting list contains only unique values from the original
list.
</p>

<h2>C# List capacity and TrimExcess</h2>

<p>
The <code>Capacity</code> property gets or sets the number of elements that the
<code>List</code> can contain. The <code>TrimExcess</code> method sets the
capacity to the actual number of elements in the list, if that number is less
than 90% of current capacity.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
List&lt;int&gt; vals = new List&lt;int&gt;(100);
Console.WriteLine($"Initial capacity: {vals.Capacity}");

vals.AddRange([1, 2, 3, 4, 5]);
Console.WriteLine($"Count: {vals.Count}");
vals.TrimExcess();
Console.WriteLine($"Trimmed capacity: {vals.Capacity}");
</pre>

<p>
This example shows how to check and set the capacity of a list. The
<code>TrimExcess</code> method reduces the capacity to match the actual number
of elements, which can help optimize memory usage.
</p>

<h2>C# List binary search</h2>

<p>
The <code>BinarySearch</code> method searches the sorted list for a specified
element and returns the zero-based index of the element in the list. If the
element is not found, a negative number is returned. The list must be sorted
before calling this method.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
List&lt;int&gt; nums = [1, 3, 5, 7, 9];
int idx = nums.BinarySearch(5);

Console.WriteLine(idx); // prints 2
</pre>

<p>
This example demonstrates how to use the <code>BinarySearch</code> method to
find the index of an element in a sorted list. If the element is found, its index
is returned; otherwise, a negative number is returned.
</p>

<h2>C# List ConvertAll: string to int</h2>

<p>
The <code>ConvertAll</code> method can be used to convert a list of one type
to another. 
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
List&lt;string&gt; numbers = ["1", "2", "3", "4"];
List&lt;int&gt; ints = numbers.ConvertAll(int.Parse);

Console.WriteLine(string.Join(", ", ints));
</pre>

<p>
This example uses <code>ConvertAll</code> to convert a list of strings
representing numbers into a list of integers. Each string is parsed to an int.
</p>


<h2>Source</h2>

<p>
<a href="https://learn.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1?view=net-8.0">List class - language reference</a>
</p>

<p>
In this article, we explored the functionality of the C# <code>List</code>
collection, learning how to efficiently store, manage, and manipulate dynamic
lists in .NET applications.
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


</html>
