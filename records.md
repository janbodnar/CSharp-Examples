
<!DOCTYPE html>
<html lang="en">
<head>
<title>C# record - explaining the record type</title>
<link rel="stylesheet" href="/cfg/style.css" type="text/css">
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="keywords" content="C#, learn C#, record, tutorial, programming language, learn C#">
<meta name="description" content="C# record tutorial shows how to work with the
record type in C#. A record is a reference type whose purpose is to hold data.">

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

<h1>C# record</h1>

<p class="last_mod">
last modified July 5, 2023
</p>
 
<p>
C# record tutorial shows how to work with the record type in C#. 
</p>


<p>
A record is a reference type whose main purpose is to hold data. It is very
useful for data analysis. The record type simplifies code and improves its
readability, and removes unnecessary boilerplate.
</p>

<p>
The record type provides the following features:
</p>

<ul>
    <li>concise syntax for data-centric objects</li>
    <li>concise syntax for immutable data</li>
    <li>value-based equality</li>
    <li>concise syntax for non-destructive mutation</li>
    <li>built-in formattting for printing</li>
</ul>

<p>
The compiler creates an override of <code>Object.Equals(Object)</code> and
<code>Object.GetHashCode</code>. It creates methods for <code>==</code> and
<code>!=</code> operators and implements the
<code>System.IEquatable&lt;T&gt;</code>. Records also provide an override of  
<code>Object.ToString</code>. 
</p>

<p>
While records share a lot of similarities with standard classes, they have
different purposes. Classes are used for defining complex hierarchies of objects
and their responsitilities, records excel in storing data for the purpose of 
their analysis.
</p>


<div class="note">
<strong>Note:</strong> The record type is an important part of the functional 
programming philosophy. It is a very useful tool for data analysis.
</div>

<p>
Important functional languages, such as F# and Clojure, have record types since
their inception. The record type appeared in C# 9.0.
</p>


<h2>C# record positional syntax</h2>

<p>
To easiest way to create a record is to use the <em>positional syntax</em>.
</p>

<pre class="compact">
record User(string FirstName, string LastName, string occupation);
</pre>

<p>
Using this syntax, the compiler automatically creates the following:
</p>

<ul>
    <li>a public init-only auto-implemented property for each positional
    parameter provided in the record declaration. </li>
    <li>a primary constructor whose parameters match the positional parameters
    on the record declaration</li>
    <li>a <code>Deconstruct</code> method with an out parameter for each
    positional parameter provided in the record declaration</li>
</ul>

<p>
The data created with positional syntax is immutable. Data immutability is an 
important cornerstone of functional programming.
</p>

<h2>C# record simple examples</h2>

<p>
In the following example, we create a simple record type.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
var users = new List&lt;User&gt;
{
    new ("John", "Doe", 1230),
    new ("Lucy", "Novak", 670),
    new ("Ben", "Walter", 2050),
    new ("Robin", "Brown", 2300),
    new ("Amy", "Doe", 1250),
    new ("Joe", "Draker", 1190),
    new ("Janet", "Doe", 980),
    new ("Albert", "Novak", 1930),
};

users.ForEach(Console.WriteLine);

Console.WriteLine(users[0].FirstName);
Console.WriteLine(users[0].LastName);
Console.WriteLine(users[0].Salary);

record User(string FirstName, string LastName, int Salary);
</pre>

<p>
We create a <code>User</code> record in one line; we are ready to use it. 
</p>

<pre class="explanation">
users.ForEach(Console.WriteLine);
</pre>

<p>
We traverse the list of users and print them to the console. Thanks to the
built-in formatting of records, we have a human-readable output for the records.
</p>

<pre class="explanation">
Console.WriteLine(users[0].FirstName);
Console.WriteLine(users[0].LastName);
Console.WriteLine(users[0].Salary);
</pre>

<p>
The properties are automatically created.
</p>

<pre class="compact">
$ dotner run
User { FirstName = John, LastName = Doe, Salary = 1230 }
User { FirstName = Lucy, LastName = Novak, Salary = 670 }
User { FirstName = Ben, LastName = Walter, Salary = 2050 }
User { FirstName = Robin, LastName = Brown, Salary = 2300 }
User { FirstName = Amy, LastName = Doe, Salary = 1250 }
User { FirstName = Joe, LastName = Draker, Salary = 1190 }
User { FirstName = Janet, LastName = Doe, Salary = 980 }
User { FirstName = Albert, LastName = Novak, Salary = 1930 }
John
Doe
1230
</pre>

<p>
In the second example, we use a record type with LINQ.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
var cars = new List&lt;Car&gt;
{
    new ("Audi", "red", 52642),
    new ("Mercedes", "blue", 57127),
    new ("Skoda", "black", 9000),
    new ("Volvo", "red", 29000),
    new ("Bentley", "yellow", 350000),
    new ("Citroen", "white", 21000),
    new ("Hummer", "black", 41400),
    new ("Volkswagen", "white", 21600),
};

var groups = from car in cars
             group car by car.Colour;

foreach (var group in groups)
{
    Console.WriteLine(group.Key);

    foreach (var car in group)
    {
        Console.WriteLine($" {car.Name} {car.Price}");
    }
}

record Car(string Name, string Colour, int Price);
</pre>

<p>
We use LINQ expression to group our cars by their colours. Again, we have
defined the record type in one line. We focus on the data analysis and not on 
complex OOP techniques.
</p>

<pre class="compact">
$ dotnet run
red
  Audi 52642
  Volvo 29000
blue
  Mercedes 57127
black
  Skoda 9000
  Hummer 41400
yellow
  Bentley 350000
white
  Citroen 21000
  Volkswagen 21600
</pre>


<h2>C# record equality</h2>

<p>
Records provide value-based equality. When we focus on data analysis, this is 
the expected behaviour. Classes on the other hand provide reference equality 
by default. To have value-based equality with classes, we have to add additional 
lines of code to the class definitions, which is often done with IDE generators
and is considered boilerplate.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
var u1 = new User("John", "Doe", "gardener");
var u2 = new User("John", "Doe", "gardener");

Console.WriteLine(u1 == u2);

var p1 = new Person("Roger", "Roe", "driver");
var p2 = new Person("Roger", "Roe", "driver");

Console.WriteLine(p1 == p2);

record User(string FirstName, string LastName, string occupation);

class Person
{
    public Person(string firstName, string lastName, string occupation)
    {
        FirstName = firstName;
        LastName = lastName;
        Occupation = occupation;
    }

    public string FirstName { get; set; }
    public string LastName { get; set; }
    public string Occupation { get; set; }
}
</pre>

<p>
In the example, we compare two records and two class objects having the same
data.
</p>

<pre class="compact">
$ dotnet run
True
False
</pre>

<p>
The records compare values while the class objects references. The second output
is False because <code>p1</code> and <code>p2</code> point to two different
objects in memory.
</p>


<h2>C# record Deconstruct</h2>

<p>
With the positional syntax, we have the <code>Deconstruct</code> method
automatically implemented. 
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
var u = new User("John", "Doe", 980);

(string fname, string lname, int sal) = u;

Console.WriteLine($"{fname} {lname} earns {sal} per month");

record User(string FirstName, string LastName, int Salary);
</pre>

<p>
A record's properties can be easily separated into variables with deconstrution
operation.
</p>

<pre class="compact">
$ dotnet run
John Doe earns 980 per month
</pre>





<h2>C# record non-destructive mutation</h2>

<p>
In functional programming, we work with immutable data. When we need to modify 
data, we create modified copies of the original data, which is intact. 
This simple rule brings huge benefits in concurrent programming.
</p>

<p>
We can use the <code>with</code> keyword to get modified copies of our records.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
var users = new List&lt;User&gt;
{
    new ("John", "Doe", 1230),
    new ("Lucy", "Novak", 670),
    new ("Ben", "Walter", 2050),
    new ("Robin", "Brown", 2300),
    new ("Amy", "Doe", 1250),
    new ("Joe", "Draker", 1190),
    new ("Janet", "Doe", 980),
    new ("Albert", "Novak", 1930),
};

var users2 = new List&lt;User&gt;();
users.ForEach(u =&gt; users2.Add(u with { Salary = u.Salary + 200 }));

users.ForEach(Console.WriteLine);

Console.WriteLine("---------------");

users2.ForEach(Console.WriteLine);

record User(string FirstName, string LastName, int Salary);
</pre>

<p>
In the example, we have a list of users. We want to add a bonus to each user.
Rather than modifying the original list, we create a new one with their salaries
modified.
</p>

<pre class="compact">
$ dotnet run
User { FirstName = John, LastName = Doe, Salary = 1230 }
User { FirstName = Lucy, LastName = Novak, Salary = 670 }
User { FirstName = Ben, LastName = Walter, Salary = 2050 }
User { FirstName = Robin, LastName = Brown, Salary = 2300 }
User { FirstName = Amy, LastName = Doe, Salary = 1250 }
User { FirstName = Joe, LastName = Draker, Salary = 1190 }
User { FirstName = Janet, LastName = Doe, Salary = 980 }
User { FirstName = Albert, LastName = Novak, Salary = 1930 }
---------------
User { FirstName = John, LastName = Doe, Salary = 1430 }
User { FirstName = Lucy, LastName = Novak, Salary = 870 }
User { FirstName = Ben, LastName = Walter, Salary = 2250 }
User { FirstName = Robin, LastName = Brown, Salary = 2500 }
User { FirstName = Amy, LastName = Doe, Salary = 1450 }
User { FirstName = Joe, LastName = Draker, Salary = 1390 }
User { FirstName = Janet, LastName = Doe, Salary = 1180 }
User { FirstName = Albert, LastName = Novak, Salary = 2130 }
</pre>


<h2>C# mutable record</h2>

<p>
It is possible to create a mutable record. However, when possible, the usage of 
immutable records is preferred.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
var u = new User("John", "Doe", "gardener");
Console.WriteLine(u);

u.Occupation = "driver";
Console.WriteLine(u);

record User
{
    public User(string firstName, string lastName, string occupation)
    {
        FirstName = firstName;
        LastName = lastName;
        Occupation = occupation;
    }
    public string FirstName { get; set; } = default!;
    public string LastName { get; set; } = default!;
    public string Occupation { get; set; } = default!;
};
</pre>

<p>
By implementing our own properties, we have a mutable record.
</p>

<pre class="compact">
$ dotnet run
User { FirstName = John, LastName = Doe, Occupation = gardener }
User { FirstName = John, LastName = Doe, Occupation = driver }
</pre>


<h2>Web scraping example</h2>

<p>
To demonstrate the usefulness of records, we have a more complex example which 
scrapes data from a website. 
</p>

<pre class="compact">
$ dotnet add package AngleSharp
$ dotnet add package CsvHelper
</pre>

<p>
We need to add the <code>AngleSharp</code> and <code>CsvHelper</code> packages 
to the project.
</p>

<div class="codehead">Program.cs
  <i class="fas fa-copy copy-icon" onclick="copyCode(this)"></i>
</div>
<pre class="code">
using System.Collections.Generic;
using System.Globalization;
using AngleSharp;
using CsvHelper;

var config = Configuration.Default.WithDefaultLoader();
using var context = BrowsingContext.New(config);

var url = "https://nrf.com/resources/top-retailers/top-100-retailers/top-100-retailers-2019";
using var doc = await context.OpenAsync(url);

var htable = doc.GetElementById("stores-list--section-16266");
var trs = htable.QuerySelectorAll("tr").Skip(1);

var csvConfig = new CsvHelper.Configuration.CsvConfiguration(CultureInfo.CurrentCulture)
{
    ShouldQuote = args =&gt; false
};

using var fs = new StreamWriter("data.csv");
using var writer = new CsvWriter(fs, csvConfig);

var rows = new List&lt;Row&gt;();

foreach (var tr in trs)
{
    var tds = tr.QuerySelectorAll("td").Take(3);
    var fields = (from e in tds select e.TextContent).ToArray();
    var row = new Row(fields[0], fields[1], fields[2]);

    rows.Add(row);
}

writer.WriteRecords(rows);

record Row(string Rank, string Company, string Sales);
</pre>

<p>
In the example, we scrape data from a website. In the HTML table, there are 
100 top retailers in the US. We connect to the website, parse the HTML table, 
and pick three of its columns. The parsed data is saved into a CSV file.
The example creates the <code>Row</code> record, which stores one row of the 
parsed data.
</p>

<h2>Source</h2>

<p>
<a href="https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/record">Records - language reference</a>
</p>

<p>
In this article we have covered C# record type. 
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
