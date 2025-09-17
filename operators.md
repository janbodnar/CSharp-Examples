# C# operators

*C# operators* are special symbols that perform operations on operands.  
Operators are fundamental building blocks in C# programming, enabling  
developers to manipulate data, perform calculations, make comparisons,  
and control program flow.

Expressions are constructed from operands and operators. The operators of an  
expression indicate which operations to apply to the operands. The order of  
evaluation of operators in an expression is determined by the *precedence*  
and *associativity* of the operators.

An *operator* is a special symbol which indicates a certain process is  
carried out. Operators in programming languages are taken from mathematics.  
Programmers work with data. The operators are used to process data. An  
*operand* is one of the inputs (arguments) of an operator.

## C# operator list

The following table shows a comprehensive set of operators used in the C#  
language.

| Category | Symbol |
|----------|--------|
| Sign operators | `+   -` |
| Arithmetic | `+   -   *   /   %` |
| Logical (boolean and bitwise) | `&   \|   ^   !   ~   &&   \|\|   true   false` |
| String concatenation | `+` |
| Increment, decrement | `++  --` |
| Shift | `<<  >>` |
| Relational | `==   !=   <   >   <=   >=` |
| Assignment | `=   +=   -=   *=   /=   %=  &=  \|=   ^=  ??=  <<=   >>=` |
| Member access | `.  ?.` |
| Indexing | `[]  ?[]` |
| Cast | `()` |
| Ternary | `?:` |
| Delegate concatenation and removal | `+  -` |
| Object creation | `new` |
| Type information | `as   is   sizeof   typeof` |
| Overflow exception control | `checked unchecked` |
| Indirection and address | `*   ->   []   &` |
| Lambda | `=>` |
| Pattern matching | `is   when` |
| Null-forgiving | `!` |
| Range | `..` |
| Index from end | `^` |

An operator usually has one or two operands. Those operators that work  
with only one operand are called *unary operators*. Those who work with  
two operands are called *binary operators*. There is also one ternary  
operator `?:`, which works with three operands.

Certain operators may be used in different contexts. For example the +  
operator. From the above table we can see that it is used in different  
cases. It adds numbers, concatenates strings or delegates; indicates the  
sign of a number. We say that the operator is *overloaded*.

## C# unary operators

C# unary operators include: +, -, ++, --, cast operator (), and negation !.

### C# sign operators

There are two sign operators: `+` and `-`. They are used to indicate or  
change the sign of a value.

```csharp
Console.WriteLine(2);
Console.WriteLine(+2);
Console.WriteLine(-2);
```

The `+` and `-` signs indicate the sign of a value. The plus sign can be  
used to indicate that we have a positive number. It can be omitted and it  
is mostly done so.

```csharp
int a = 1;
Console.WriteLine(-a);
Console.WriteLine(-(-a));
```

The minus sign changes the sign of a value.

```
$ dotnet run
-1
1
```

### C# increment and decrement operators

Incrementing or decrementing a value by one is a common task in programming.  
C# has two convenient operators for this: `++` and `--`.

```
x++;
x = x + 1;
...
y--;
y = y - 1;
```

The above two pairs of expressions do the same.

```csharp
int x = 6;

x++;
x++;

Console.WriteLine(x);

x--;
Console.WriteLine(x);
```

In the above example, we demonstrate the usage of both operators.

```csharp
int x = 6;

x++;
x++;
```

We initiate the `x` variable to 6. Then we increment `x` two times. Now  
the variable equals to 8.

```csharp
x--;
```

We use the decrement operator. Now the variable equals to 7.

```
$ dotnet run
8
7
```

### C# explicit cast operator

The explicit cast operator () can be used to cast a type to another type.  
Note that this operator works only on certain types.

```csharp
float val = 3.2f;
int num = (int) val;

Console.WriteLine(num);
```

In the example, we explicitly cast a `float` type to `int`.

### Negation operator

The negation operator (!) reverses the meaning of its operand.

```csharp
var isValid = false;

if (!isValid)
{
    Console.WriteLine("The option is not valid");
}
```

In the example, we build a negative condition: it is executed if the inverse  
of the expression is valid.

## C# assignment operator

The assignment operator `=` assigns a value to a variable. A *variable* is  
a placeholder for a value. In mathematics, the `=` operator has a different  
meaning. In an equation, the `=` operator is an equality operator. The left  
side of the equation is equal to the right one.

```
int x = 1;
```

Here we assign a number to the `x` variable.

```
x = x + 1;
```

The previous expression does not make sense in mathematics. But it is legal  
in programming. The expression adds 1 to the `x` variable. The right side  
is equal to 2 and 2 is assigned to `x`.

```
3 = x;
```

This code example results in syntax error. We cannot assign a value to  
a literal.

## C# concatenating strings

The + operator is also used to concatenate strings.

```csharp
Console.WriteLine("Return " + "of " + "the king.");
```

We join three strings together using string concatenation operator.

```
$ dotnet run
Return of the king.
```

## C# arithmetic operators

The following is a table of arithmetic operators in C#.

| Symbol | Name |
|--------|------|
| `+` | Addition |
| `-` | Subtraction |
| `*` | Multiplication |
| `/` | Division |
| `%` | Remainder |

The following example shows arithmetic operations.

```csharp
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
```

In the preceding example, we use addition, subtraction, multiplication,  
division, and remainder operations. This is all familiar from the mathematics.

```csharp
int rem = c % a;
```

The `%` operator is called the remainder or the modulo operator. It finds  
the remainder of division of one number by another. For example, `9 % 4`,  
9 modulo 4 is 1, because 4 goes into 9 twice with a remainder of 1.

```
$ dotnet run
33
2
110
4
2
```

Next we show the distinction between integer and floating point division.

```csharp
int c = 5 / 2;
Console.WriteLine(c);

double d = 5 / 2.0;
Console.WriteLine(d);
```

In the preceding example, we divide two numbers.

```csharp
int c = 5 / 2;
```

This code example results in integer division. The result is 2.

```csharp
double d = 5 / 2.0;
```

If one of the operands is a double, we have a floating point division and  
the result is 2.5.

```
$ dotnet run
2
2.5
```

## C# Boolean operators

In C#, we have three logical operators. The `bool` keyword is used to  
declare a Boolean value.

| Symbol | Name |
|--------|------|
| `&&` | logical and |
| `\|\|` | logical or |
| `!` | negation |

Boolean operators are also called logical.

```csharp
int x = 3;
int y = 8;

Console.WriteLine(x == y);
Console.WriteLine(y > x);

if (y > x)
{
    Console.WriteLine("y is greater than x");
}
```

Many expressions result in a boolean value. Boolean values are used in  
conditional statements.

```csharp
Console.WriteLine(x == y);
Console.WriteLine(y > x);
```

Relational operators always result in a boolean value. These two lines  
print false and true.

```csharp
if (y > x)
{
    Console.WriteLine("y is greater than x");
}
```

The body of the `if` statement is executed only if the condition inside  
the parentheses is met. The `y > x` returns true, so the message  
"y is greater than x" is printed to the terminal.

The `true` and `false` keywords represent boolean literals in C#.

```csharp
bool a = true && true;
bool b = true && false;
bool c = false && true;
bool d = false && false;

Console.WriteLine(a);
Console.WriteLine(b);
Console.WriteLine(c);
Console.WriteLine(d);
```

Example shows the logical and operator. It evaluates to true only if both  
operands are true.

```
$ dotnet run
True
False
False
False
```

Only one expression results in `True`.

The logical or `||` operator evaluates to true, if either of the operands  
is true.

```csharp
bool a = true || true;
bool b = true || false;
bool c = false || true;
bool d = false || false;

Console.WriteLine(a);
Console.WriteLine(b);
Console.WriteLine(c);
Console.WriteLine(d);
```

If one of the sides of the operator is true, the outcome of the operation  
is true.

```
$ dotnet run
True
True
True
False
```

Three of four expressions result in true.

The negation operator `!` makes true false and false true.

```csharp
Console.WriteLine(!true);
Console.WriteLine(!false);
Console.WriteLine(!(4 < 3));
```

The example shows the negation operator in action.

```
$ dotnet run
False
True
True
```

The `||`, and `&&` operators are short circuit evaluated. *Short circuit  
evaluation* means that the second argument is only evaluated if the first  
argument does not suffice to determine the value of the expression: when  
the first argument of the logical and evaluates to false, the overall value  
must be false; and when the first argument of logical or evaluates to true,  
the overall value must be true. Short circuit evaluation is used mainly to  
improve performance.

An example may clarify this a bit more.

```csharp
Console.WriteLine("Short circuit");

if (One() && Two())
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
```

We have two methods in the example. They are used as operands in boolean  
expressions.

```csharp
if (One() && Two())
{
    Console.WriteLine("Pass");
}
```

The `One` method returns `false`. The short circuit && does not evaluate  
the second method. It is not necessary. Once an operand is `false`, the  
result of the logical conclusion is always `false`. Only "Inside one" is  
only printed to the console.

```csharp
Console.WriteLine("#############");

if (Two() || One())
{
    Console.WriteLine("Pass");
}
```

In the second case, we use the `||` operator and use the `Two` method as  
the first operand. In this case, "Inside two" and "Pass" strings are  
printed to the terminal. It is again not necessary to evaluate the second  
operand, since once the first operand evaluates to `true`, the logical or  
is always `true`.

```
$ dotnet run
Short circuit
Inside one
#############
Inside two
Pass
```

## C# relational operators

Relational operators are used to compare values. These operators always  
result in boolean value.

| Symbol | Meaning |
|--------|---------|
| `<` | less than |
| `<=` | less than or equal to |
| `>` | greater than |
| `>=` | greater than or equal to |
| `==` | equal to |
| `!=` | not equal to |

Relational operators are also called comparison operators.

```csharp
Console.WriteLine(3 < 4);
Console.WriteLine(3 == 4);
Console.WriteLine(4 >= 3);
Console.WriteLine(4 != 3);
```

In the code example, we have four expressions. These expressions compare  
integer values. The result of each of the expressions is either true or  
false. In C# we use `==` to compare numbers. Some languages like Ada,  
Visual Basic, or Pascal use `=` for comparing numbers.

## C# bitwise operators

Decimal numbers are natural to humans. Binary numbers are native to  
computers. Binary, octal, decimal, or hexadecimal symbols are only  
notations of the same number. Bitwise operators work with bits of a binary  
number. Bitwise operators are seldom used in higher level languages like C#.

| Symbol | Meaning |
|--------|---------|
| `~` | bitwise negation |
| `^` | bitwise exclusive or |
| `&` | bitwise and |
| `\|` | bitwise or |

The *bitwise negation operator* changes each 1 to 0 and 0 to 1.

```
Console.WriteLine(~ 7); // prints -8
Console.WriteLine(~ -8); // prints 7
```

The operator reverts all bits of a number 7. One of the bits also determines,  
whether the number is negative or not. If we negate all the bits one more  
time, we get number 7 again.

The *bitwise and operator* performs bit-by-bit comparison between two  
numbers. The result for a bit position is 1 only if both corresponding  
bits in the operands are 1.

```
      00110
   &  00011
   =  00010
```

The first number is a binary notation of 6, the second is 3, and the  
result is 2.

```
Console.WriteLine(6 & 3); // prints 2
Console.WriteLine(3 & 6); // prints 2
```

The *bitwise or operator* performs bit-by-bit comparison between two  
numbers. The result for a bit position is 1 if either of the corresponding  
bits in the operands is 1.

```
     00110
   | 00011
   = 00111
```

The result is `00110` or decimal 7.

```
Console.WriteLine(6 | 3); // prints 7
Console.WriteLine(3 | 6); // prints 7
```

The *bitwise exclusive or operator* performs bit-by-bit comparison between  
two numbers. The result for a bit position is 1 if one or the other (but  
not both) of the corresponding bits in the operands is 1.

```
      00110
   ^  00011
   =  00101
```

The result is `00101` or decimal 5.

```
Console.WriteLine(6 ^ 3); // prints 5
Console.WriteLine(3 ^ 6); // prints 5
```

## C# compound assignment operators

The compound assignment operators consist of two operators. They are  
shorthand operators.

```
a = a + 3;
a += 3;
```

The `+=` compound operator is one of these shorthand operators. The above  
two expressions are equal. Value 3 is added to the a variable.

Other compound operators are:

```
-=   *=   /=   %=   &=   |=   <<=   >>=
```

```csharp
int a = 1;
a = a + 1;

Console.WriteLine(a);

a += 5;
Console.WriteLine(a);

a *= 3;
Console.WriteLine(a);
```

In the example, we use two compound operators.

```csharp
int a = 1;
a = a + 1;
```

The `a` variable is initiated to one. 1 is added to the variable using  
the non-shorthand notation.

```csharp
a += 5;
```

Using a `+=` compound operator, we add 5 to the `a` variable. The statement  
is equal to `a = a + 5;`.

```csharp
a *= 3;
```

Using the `*=` operator, the `a` is multiplied by 3. The statement is  
equal to `a = a * 3;`.

```
$ dotnet run
2
7
21
```

## C# new operator

The `new` operator is used to create objects and invoke constructors.

```csharp
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
```

In the example, we create a new custom object and a array of integers  
utilizing the `new` operator.

```csharp
public Being()
{
    Console.WriteLine("Being created");
}
```

This is a constructor. It is called at the time of the object creation.

## C# access operator

The access operator `[]` is used with arrays, indexers, and attributes.

```csharp
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
```

In the example, we use the `[]` operator to get an element of an array,  
value of a dictionary pair, and activate a built-in attribute.

```csharp
var vals = new int[] { 2, 4, 6, 8, 10 };
Console.WriteLine(vals[0]);
```

We define an array of integers. We get the first element with `vals[0]`.

```csharp
var domains = new Dictionary<string, string>()
{
    { "de", "Germany" },
    { "sk", "Slovakia" },
    { "ru", "Russia" }
};

Console.WriteLine(domains["de"]);
```

A dictionary is created. With `domains["de"]`, we get the value of the  
pair that has the `"de"` key.

```csharp
[Obsolete("Don't use OldMethod, use NewMethod instead", false)]
void oldMethod()
{
    Console.WriteLine("oldMethod()");
}
```

We active the built-in `Obsolete` attribute. The attribute issues a warning.

When we run the program, it produces the warning:  
`warning CS0618: 'oldMethod()' is obsolete: 'Don't use OldMethod, use NewMethod instead'`.

## C# index from end operator ^

The index from end operator ^ indicates the element position from the end  
of a sequence. For instance, `^1` points to the last element of a sequence  
and `^n` points to the element with offset `length - n`.

```csharp
int[] vals = { 1, 2, 3, 4, 5 };

Console.WriteLine(vals[^1]);
Console.WriteLine(vals[^2]);

var word = "gray falcon";

Console.WriteLine(word[^1]);
```

In the example, we apply the operator on an array and a string.

```csharp
int[] vals = { 1, 2, 3, 4, 5 };

Console.WriteLine(vals[^1]);
Console.WriteLine(vals[^2]);
```

We print the last and the last but one element of the array.

```csharp
var word = "gray falcon";

Console.WriteLine(word[^1]);
```

We print the last letter of the word.

```
$ dotnet run
5
4
n
```

## C# range operator ..

The `..` operator specifies the start and end of a range of indices as  
its operands. The left-hand operand is an inclusive start of a range.  
The right-hand operand is an exclusive end of a range.

```
x.. is equivalent to x..^0
..y is equivalent to 0..y
.. is equivalent to 0..^0
```

Operands of the `..` operator can be omitted to get an open-ended range.

```csharp
int[] vals = { 1, 2, 3, 4, 5, 6, 7 };

var slice1 = vals[1..4];
Console.WriteLine("[{0}]", string.Join(", ", slice1));

var slice2 = vals[..^0];
Console.WriteLine("[{0}]", string.Join(", ", slice2));
```

In the example, we use the `..` operator to get array slices.

```csharp
var slice1 = vals[1..4];
Console.WriteLine("[{0}]", string.Join(", ", slice1));
```

We create an array slice from index 1 till index 4; the last index 4  
is not included.

```csharp
var slice2 = vals[..^0];
Console.WriteLine("[{0}]", string.Join(", ", slice2));
```

Here we essentially create a copy of the array.

```
$ dotnet run
[2, 3, 4]
[1, 2, 3, 4, 5, 6, 7]
```

## C# type information

Now we concern ourselves with operators that work with types.

The `sizeof` operator is used to obtain the size in bytes for a value  
type. The `typeof` is used to obtain the `System.Type` object for a type.

```csharp
Console.WriteLine(sizeof(int));
Console.WriteLine(sizeof(float));
Console.WriteLine(sizeof(Int32));

Console.WriteLine(typeof(int));
Console.WriteLine(typeof(float));
```

We use the `sizeof` and `typeof` operators.

```
$ dotnet run
4
4
4
System.Int32
System.Single
```

We can see that the `int` type is an alias for `System.Int32` and the  
`float` is an alias for the `System.Single` type.

The `is` operator checks if an object is compatible with a given type.

```csharp
Base _base = new Base();
Derived derived = new Derived();

Console.WriteLine(_base is Base);
Console.WriteLine(_base is Object);
Console.WriteLine(derived is Base);
Console.WriteLine(_base is Derived);

class Base { }
class Derived : Base { }
```

We create two objects from user defined types.

```csharp
class Base { }
class Derived : Base { }
```

We have a `Base` and a `Derived` class. The `Derived` class inherits  
from the `Base` class.

```csharp
Console.WriteLine(_base is Base);
Console.WriteLine(_base is Object);
```

`Base` equals `Base` and so the first line prints True. The `Base` is  
also compatible with `Object` type. This is because each class inherits  
from the mother of all classes — the `Object` class.

## C# null-conditional operator

A *null-conditional operator* applies a member access, `?.`, or element  
access, `?[]`, operation to its operand only if that operand evaluates to  
non-null. If the operand evaluates to `null`, the result of applying the  
operator is null.

```csharp
var users = new List<User>() { new User("John Doe", "gardener"), new User(null, null),
        new User("Lucia Newton", "teacher") };

users.ForEach(user => Console.WriteLine(user.Name?.ToUpper()));

record User(string? Name, string? Occupation);
```

In the example, we have a `User` class with two members: `Name` and  
`Occupation`. We access the `name` member of the objects with the help  
of the `?.` operator.

```csharp
var users = new List<User>() { new User("John Doe", "gardener"), new User(null, null),
        new User("Lucia Newton", "teacher") };
```

We have a list of users. One of them is initialized with null values.

```csharp
users.ForEach(user => Console.WriteLine(user.Name?.ToUpper()));
```

We use the `?.` to access the `Name` member and call the `ToUpper` method.  
The `?.` prevents the `System.NullReferenceException` by not calling the  
`ToUpper` on the `null` value.

```
$ dotnet run
JOHN DOE

LUCIA NEWTON
```

In the following example, we use the `?[]` operator. The operator allows  
to place `null` values into a collection.

```csharp
int?[] vals = { 1, 2, 3, null, 4, 5 };

int i = 0;

while (i < vals.Length)
{
    Console.WriteLine(vals[i]?.GetType());
    i++;
}
```

In this example, we have a `null` value in an array. We prevent the  
`System.NullReferenceException` by applying the `?.` operator on the  
array elements.

## C# null-coalescing operator

The null-coalescing operator `??` is used to define a default value for  
a `nullable` type. It returns the left-hand operand if it is not null;  
otherwise it returns the right operand. When we work with databases, we  
often deal with absent values. These values come as nulls to the program.  
This operator is a convenient way to deal with such situations.

```csharp
int? x = null;
int? y = null;

int z = x ?? y ?? -1;

Console.WriteLine(z);
```

An example program for null-coalescing operator.

```csharp
int? x = null;
int? y = null;
```

Two nullable `int` types are initiated to `null`. The `int?` is a  
shorthand for `Nullable<int>`. It allows to have null values assigned  
to `int` types.

```csharp
int z = x ?? y ?? -1;
```

We want to assign a value to `z` variable. But it must not be `null`.  
This is our requirement. We can easily use the null-coalescing operator  
for that. In case both `x` and `y` variables are null, we assign -1 to `z`.

```
$ dotnet run
-1
```

## C# null-coalescing assignment operator

The null-coalescing assignment operator `??=` assigns the value of its  
right-hand operand to its left-hand operand only if the left-hand operand  
evaluates to `null`. The `??=` operator does not evaluate its right-hand  
operand if the left-hand operand evaluates to non-null. It is available  
in C# 8.0 and later.

```csharp
List<int> vals = null;

vals ??= new List<int>() {1, 2, 3, 4, 5, 6};
vals.Add(7);
vals.Add(8);
vals.Add(9);

Console.WriteLine(string.Join(", ", vals));

vals ??= new List<int>() {1, 2, 3, 4, 5, 6};

Console.WriteLine(string.Join(", ", vals));
```

In the example, we use the null-coalescing assignment operator on a list  
of integer values.

```csharp
List<int> vals = null;
```

First, the list is assigned to `null`.

```csharp
vals ??= new List<int>() {1, 2, 3, 4, 5, 6};
vals.Add(7);
vals.Add(8);
vals.Add(9);

Console.WriteLine(string.Join(", ", vals));
```

We use the null-coalescing assignment operator to assign a new list to  
the `vals` variable. Since it is `null`, the list is assigned. Then we  
add some values to the list and print its contents.

```csharp
vals ??= new List<int>() {1, 2, 3, 4, 5, 6};
```

We try to assign a new list object to the variable. Since the variable  
is not `null` anymore, the list is not assigned.

```
$ dotnet run
1, 2, 3, 4, 5, 6, 7, 8, 9
1, 2, 3, 4, 5, 6, 7, 8, 9
```

## C# operator precedence

The *operator precedence* tells us which operators are evaluated first.  
The precedence level is necessary to avoid ambiguity in expressions.

What is the outcome of the following expression, 28 or 40?

```
3 + 5 * 5
```

Like in mathematics, the multiplication operator has a higher precedence  
than addition operator. So the outcome is 28.

```
(3 + 5) * 5
```

To change the order of evaluation, we can use parentheses. Expressions  
inside parentheses are always evaluated first.

The following table shows common C# operators ordered by precedence  
(highest precedence first):

| Operator(s) | Category | Associativity |
|-------------|----------|---------------|
| Primary | `x.y  x?.y, x?[y] f(x)  a[x]  x++  x--  new  typeof  default  checked  unchecked` | Left |
| Unary | `+  -  !  ~  ++x  --x  (T)x` | Left |
| Multiplicative | `* / %` | Left |
| Additive | `+ -` | Left |
| Shift | `<< >>` | Left |
| Equality | `== !=` | Right |
| Logical AND | `&` | Left |
| Logical XOR | `^` | Left |
| Logical OR | `\|` | Left |
| Conditional AND | `&&` | Left |
| Conditional OR | `\|\|` | Left |
| Null Coalescing | `??` | Left |
| Ternary | `?:` | Right |
| Assignment | `=  *=  /=  %=  +=  -=  <<=  >>=  &=  ^=  \|=  ??=  =>` | Right |

Operators on the same row of the table have the same precedence.

```csharp
Console.WriteLine(3 + 5 * 5);
Console.WriteLine((3 + 5) * 5);

Console.WriteLine(! true | true);
Console.WriteLine(! (true | true));
```

In this code example, we show a few expressions. The outcome of each  
expression is dependent on the precedence level.

```csharp
Console.WriteLine(3 + 5 * 5);
```

This line prints 28. The multiplication operator has a higher precedence  
than addition. First, the product of `5*5` is calculated, then 3 is added.

```csharp
Console.WriteLine(! true | true);
```

This line prints True. The negation operator has a higher precedence than  
the bitwise or. First, `!true` is evaluated to `false`, then `false | true`  
is evaluated to `true`.

```
$ dotnet run
28
40
True
False
```

## C# ternary operator

The ternary operator `?:` is a conditional operator. It is a convenient  
operator for cases where we want to pick up one of two values, depending  
on the outcome of a Boolean expression.

```csharp
int age = 31;

bool adult = age >= 18 ? true : false;
Console.WriteLine($"Adult: {adult}");
```

First we assign a value to the age variable. Then we use the ternary  
operator. If the age variable is greater than or equal to 18, the value  
after the `?` character is returned. If not, the value after the `:`  
character is returned. The returned value is then assigned to the adult  
variable.

```
$ dotnet run
Adult: True
```

## C# lambda operator

The lambda operator `=>` is used to create lambda expressions. Lambda  
expressions are used to create anonymous functions or expression trees.  
The left side of the `=>` operator specifies the input parameters and  
the right side holds the expression or statement block.

```csharp
var nums = new List<int> { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

// Lambda expression to filter even numbers
var evenNums = nums.Where(x => x % 2 == 0);
Console.WriteLine($"Even numbers: {string.Join(", ", evenNums)}");

// Lambda expression to calculate squares
var squares = nums.Select(x => x * x);
Console.WriteLine($"Squares: {string.Join(", ", squares)}");
```

In this example, we use lambda expressions with LINQ methods to filter  
and transform data.

```
$ dotnet run
Even numbers: 2, 4, 6, 8, 10
Squares: 1, 4, 9, 16, 25, 36, 49, 64, 81, 100
```

## C# pattern matching operators

C# provides several operators for pattern matching, which is a powerful  
feature for testing expressions and performing actions based on their  
structure.

### C# is pattern operator

The `is` operator tests if an expression matches a pattern.

```csharp
object obj = "Hello, World!";

if (obj is string str)
{
    Console.WriteLine($"String length: {str.Length}");
}

if (obj is string { Length: > 10 })
{
    Console.WriteLine("Long string detected");
}
```

### C# switch expressions

Switch expressions provide a more concise way to perform pattern matching.

```csharp
string GetDayType(int day) => day switch
{
    1 or 2 or 3 or 4 or 5 => "Weekday",
    6 or 7 => "Weekend",
    _ => "Invalid day"
};

Console.WriteLine(GetDayType(3)); // Weekday
Console.WriteLine(GetDayType(7)); // Weekend
```

## C# null-forgiving operator

The null-forgiving operator `!` suppresses nullable warnings when you  
know that a value cannot be null, even though the compiler thinks it might be.

```csharp
string? name = GetName(); // Method might return null
Console.WriteLine(name!.Length); // ! tells compiler name is not null
```

**Note:** Use this operator carefully as it can lead to runtime exceptions  
if the value is actually null.

## C# await operator

The `await` operator is used in asynchronous programming to suspend  
execution of an async method until the awaited task completes.

```csharp
using System.Net.Http;

var client = new HttpClient();
string response = await client.GetStringAsync("https://api.github.com");
Console.WriteLine($"Response length: {response.Length}");
```

The `await` operator can only be used inside methods marked with the  
`async` keyword.

## Shift operators

The shift operators `<<` and `>>` move bits left or right in binary  
representations of numbers.

```csharp
int num = 8; // Binary: 1000

int leftShift = num << 2;  // Shift left by 2: 100000 (32)
int rightShift = num >> 2; // Shift right by 2: 10 (2)

Console.WriteLine($"Original: {num}");
Console.WriteLine($"Left shift << 2: {leftShift}");
Console.WriteLine($"Right shift >> 2: {rightShift}");
```

```
$ dotnet run
Original: 8
Left shift << 2: 32
Right shift >> 2: 2
```
