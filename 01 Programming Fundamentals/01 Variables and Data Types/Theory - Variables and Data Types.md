# C# Academy
# Module 01 – Programming Fundamentals
# Topic 01 – Variables and Data Types

> **Difficulty:** Beginner
>
> **Prerequisites:** None
>
> **Estimated Reading Time:** 35–45 Minutes
>
> **Estimated Practice Time:** 2–3 Hours

---

# Learning Objectives

After completing this chapter, you will be able to:

- Explain what data is.
- Explain why variables exist.
- Choose the correct data type.
- Declare and initialize variables.
- Understand how variables are stored (conceptually).
- Follow Microsoft's naming conventions.
- Avoid common beginner mistakes.
- Understand what happens behind the scenes when a variable is created.
- Decide between different numeric data types.
- Write clean and readable variable declarations.

---

# Big Picture

Programming is nothing more than **giving instructions to a computer**.

Every instruction either

- stores data,
- processes data,
- or displays data.

Before doing anything, the computer must remember information.

Imagine creating a **Student Management System**.

The computer needs to remember

- Student Name
- Roll Number
- Age
- Percentage
- Attendance
- Phone Number

Without memory, none of this is possible.

This is where **Variables** come into the picture.

```
                Real World

                     │
                     ▼

          Information to Remember

                     │
                     ▼

               Variables

                     │
                     ▼

        What kind of information?

                     │
                     ▼

                Data Types

                     │
                     ▼

             Processing Begins
```

---

# Why Do Variables Exist?

Imagine writing this program.

```csharp
Console.WriteLine("Rahul");
Console.WriteLine(25);
Console.WriteLine(95.4);
```

It works.

Now imagine the student's age changes.

```
25 → 26
```

You now have to search your entire program.

If the value appears 200 times...

You must change it 200 times.

That is inefficient.

Instead we do this.

```csharp
int age = 25;

Console.WriteLine(age);
```

Now changing

```csharp
age = 26;
```

automatically updates every place that uses the variable.

**Variables make programs flexible.**

---

# Real-World Analogy

Imagine your house.

Every room contains boxes.

Each box has

- a label
- and something stored inside.

```
+------------------------+
| Label : Age            |
|------------------------|
| Value : 25             |
+------------------------+

+------------------------+
| Label : Name           |
|------------------------|
| Value : Rahul          |
+------------------------+
```

Programming works exactly the same way.

Variable Name = Label

Variable Value = Content inside the box

Data Type = What kind of box it is

---

# What is a Variable?

## Definition

A **Variable** is a named storage location used to store data that can change during program execution.

Microsoft's idea is simple.

```
Variable

↓

Named Memory Location

↓

Stores Value

↓

Value can change
```

Example

```csharp
int age = 25;
```

Here

```
age
```

is the variable.

```
25
```

is the value.

```
int
```

is the data type.

---

# What is a Data Type?

A computer only understands **binary (0 and 1)**.

It cannot understand

```
25

"Aman"

True

98.5
```

unless we tell it **what kind of data** it is.

That is the purpose of a **Data Type**.

```
Data

        │

        ▼

Whole Number ?

        │

 ┌──────┴──────┐

Yes            No

│              │

▼              ▼

int       Decimal?

               │

       ┌───────┴───────┐

      Yes             No

       │               │

       ▼               ▼

double            string/char/bool
```

---

# Relationship Between Variables and Data Types

A variable cannot exist without a data type.

```
int age;

string name;

double marks;

bool passed;
```

Think of it like this.

```
Variable

↓

Needs a Data Type

↓

Data Type decides

• Memory Size

• Allowed Values

• Operations
```

---

# Variable Declaration

Declaration means

**telling the compiler that a variable exists.**

Syntax

```csharp
dataType variableName;
```

Example

```csharp
int age;
```

Meaning

```
Compiler

↓

Reserve space

↓

Variable Name

↓

age

↓

Type

↓

int
```

---

# Variable Initialization

Initialization means

**giving the variable its first value.**

```csharp
int age = 25;
```

Here

```
Declaration ✔

Initialization ✔
```

Both happen together.

---

# Assignment

Assignment means

changing the value later.

```csharp
age = 30;
```

Notice

```
Declaration

↓

Only Once
```

Assignment

```
↓

Many Times
```

---

# Variable Life Cycle

```
Need Information

        │

        ▼

Choose Data Type

        │

        ▼

Declare Variable

        │

        ▼

Initialize Variable

        │

        ▼

Read Value

        │

        ▼

Modify Value

        │

        ▼

Program Ends
```

---

# Behind the Scenes

When you write

```csharp
int age = 25;
```

The compiler performs several checks:

✔ Is `int` a valid type?

✔ Is `age` a valid identifier?

✔ Can the value `25` fit inside an `int`?

✔ Is there any syntax error?

If everything is valid,

the program is compiled.

When the program runs, the CLR allocates storage for the variable according to its scope and type, initializes it with the value `25`, and allows your code to read or modify it during execution.

You don't have to manage this memory manually—that's one of C#'s strengths.

---

# Why Can't We Skip the Data Type?

Suppose we write

```csharp
age = 25;
```

Question:

Where should the computer store it?

```
1 byte?

2 bytes?

4 bytes?

8 bytes?

16 bytes?
```

The computer has no idea.

Therefore this is invalid.

A data type is mandatory because it tells the compiler **how much memory is needed and what kind of value is being stored.**

---

# What Happens If...?

## What happens if we don't initialize a local variable?

```csharp
int age;

Console.WriteLine(age);
```

❌ Compile-time error.

**Why?**

C# prevents you from reading an uninitialized local variable because it could contain an undefined value.

---

## What happens if we initialize it?

```csharp
int age = 25;

Console.WriteLine(age);
```

✅ Works perfectly.

---

## What happens if we change the value?

```csharp
int age = 25;

age = 40;
```

Now the variable stores

```
40
```

The previous value is replaced.

Variables are called **variables** because their values can vary.

---

## What happens if we declare the same variable twice?

```csharp
int age;

int age;
```

❌ Compile-time error.

Every variable name must be unique within the same scope.

---

# Classification of Variables

Variables in C# are classified based on **where they are declared** and **how long they live**.

```
Variables
│
├── Local Variables
├── Instance Variables (Fields)
├── Static Variables
├── Parameters
└── Constants
```

> **Note**
>
> In this chapter, we will focus primarily on **Local Variables** because they are the first type every C# programmer learns.
>
> The remaining types will be covered in detail in later chapters.

---

# 1. Local Variables

A **Local Variable** is declared inside a method, constructor, or block.

```csharp
static void Main()
{
    int age = 25;
}
```

The variable exists only inside that block.

```
Main()

{

    age

}

↓

Program Ends

↓

age Destroyed
```

### Real Life Example

Imagine writing something on a classroom whiteboard.

When the class ends,

the board is cleaned.

The information disappears.

Local variables behave the same way.

---

# 2. Instance Variables (Preview)

Declared inside a class.

```csharp
class Student
{
    int age;
}
```

Every object gets its own copy.

We'll study this in the **Classes** chapter.

---

# 3. Static Variables (Preview)

```csharp
class Student
{
    static int totalStudents;
}
```

Only one copy exists.

Shared by every object.

---

# 4. Parameters (Preview)

```csharp
void PrintAge(int age)
{
}
```

Used to receive information into methods.

---

# 5. Constants (Preview)

```csharp
const double PI = 3.1415926535;
```

Cannot be changed.

Useful for fixed values.

---

# Classification of Data Types

Every value in C# belongs to some data type.

```
Data Types

│

├── Value Types

│      │

│      ├── Integral

│      ├── Floating Point

│      ├── Decimal

│      ├── Character

│      └── Boolean

│

└── Reference Types

       │

       ├── string

       ├── object

       ├── arrays

       └── classes
```

> **Important**
>
> We will learn **Value Types vs Reference Types** deeply in the Object-Oriented Programming module.
>
> For now, simply remember that C# groups data this way.

---

# Integral Types (Whole Numbers)

Used to store numbers **without decimal points**.

| Type | Size | Range | Common Use |
|------|------|--------|------------|
| byte | 1 byte | 0 to 255 | Images, binary data |
| sbyte | 1 byte | -128 to 127 | Rare |
| short | 2 bytes | ±32K | Small numbers |
| ushort | 2 bytes | 0 to 65K | Rare |
| int | 4 bytes | ±2.1 Billion | ⭐ Default integer |
| uint | 4 bytes | Positive only | Rare |
| long | 8 bytes | Huge | Large IDs |
| ulong | 8 bytes | Very huge | Rare |

---

## Which integer should I use?

```
Need Whole Number

        │

        ▼

Within ±2 Billion ?

        │

 ┌──────┴──────┐

      Yes      No

       │        │

       ▼        ▼

      int      long
```

### Professional Tip

For almost every application,

```
int
```

is the correct choice.

Microsoft itself uses `int` extensively.

---

# What Happens If...

## Using long instead of int

```csharp
long age = 25;
```

Works?

✅ Yes

Recommended?

Usually ❌ No.

Reason

- More memory
- No practical benefit
- Makes code less consistent

Use `long` only when values may exceed the range of `int`.

---

## Using byte for age

```csharp
byte age = 25;
```

Works?

✅ Yes

Should you?

Usually ❌ No.

Reason

Today's age fits.

Tomorrow requirements may change.

Using `int` avoids unnecessary restrictions.

---

# Floating Point Types

Used to store decimal numbers.

| Type | Size | Precision | Use |
|------|------|-----------|-----|
| float | 4 Bytes | ~7 digits | Graphics, games |
| double | 8 Bytes | ~15 digits | Scientific calculations |
| decimal | 16 Bytes | High precision | Money |

---

# Decision Tree

```
Need Decimal Number?

        │

        ▼

Money?

   │

 ┌─┴─────┐

Yes      No

│         │

▼         ▼

decimal   Scientific?

              │

       ┌──────┴──────┐

      Yes          No

       │            │

       ▼            ▼

    double        float
```

---

# What Happens If...

## Using float for money

```csharp
float price = 10.25f;
```

Works?

✅ Yes.

Recommended?

❌ No.

Why?

Floating-point numbers cannot exactly represent many decimal values.

Example

```
10.25

may internally become

10.249999...
```

Small rounding errors accumulate in financial calculations.

Always use

```csharp
decimal
```

for currency.

---

## Using decimal for scientific calculations

Works?

✅ Yes.

Recommended?

Usually ❌ No.

Reason

`decimal` is designed for precision, not speed.

Scientific calculations generally use

```csharp
double
```

because it is faster and provides sufficient precision.

---

# Character Type

Stores **exactly one Unicode character**.

```csharp
char grade = 'A';
```

Notice

Single quotes

```
'A'
```

---

# What Happens If...

```csharp
char grade = "A";
```

❌ Compile-time error.

Why?

```
"A"
```

is a string.

```
'A'
```

is a character.

They are different data types.

---

# Boolean Type

Stores only two values.

```csharp
bool passed = true;
```

Possible values

```
true

false
```

Nothing else.

---

# What Happens If...

```csharp
bool passed = 1;
```

❌ Compile-time error.

Unlike C or C++,

C# does **not** automatically convert integers into booleans.

This avoids many programming bugs.

---

# String Type

Stores text.

```csharp
string name = "Rahul";
```

```
Name

↓

R

a

h

u

l
```

A string is a sequence of characters.

---

# What Happens If...

```csharp
string age = "25";
```

Works?

✅ Yes.

Can we calculate?

```csharp
age + 5
```

❌ Not mathematically.

The result becomes

```
255
```

because strings are concatenated.

If you want calculations,

convert it to an integer first.

```csharp
int age = 25;
```

---

# object Type

`object` is the root type of all C# types.

It can store almost anything.

```csharp
object value;

value = 25;

value = "Rahul";

value = true;
```

Useful?

Yes.

Recommended for everyday programming?

Usually ❌ No.

Specific types (`int`, `string`, `double`, etc.) are clearer and safer.

---

# var Keyword

```csharp
var age = 25;
```

Does `var` mean "no data type"?

**No.**

The compiler automatically determines the type.

```
var age = 25;

↓

Compiler

↓

int age = 25;
```

---

# What Happens If...

```csharp
var age;
```

❌ Compile-time error.

Why?

The compiler cannot infer the type because no value is provided.

Correct

```csharp
var age = 25;
```

---

## What Happens If...

```csharp
var age = 25;

age = "Rahul";
```

❌ Compile-time error.

Although `var` looks flexible,

the inferred type is still

```csharp
int
```

It cannot later become a string.

---

# Variable Naming Rules

A variable name must follow certain rules. These are enforced by the C# compiler.

| Rule | Example | Valid |
|------|---------|-------|
| Must start with a letter or `_` | `age`, `_count` | ✅ |
| Cannot start with a number | `2age` | ❌ |
| Can contain digits after first character | `student1` | ✅ |
| No spaces allowed | `student age` | ❌ |
| No special characters | `age@` | ❌ |
| Case Sensitive | `Age` and `age` | ✅ Different variables |
| Cannot use C# keywords | `int int;` | ❌ |

---

# Examples

## ✔ Valid Variable Names

```csharp
int age;
string studentName;
double averageMarks;
bool isPassed;
decimal accountBalance;
```

---

## ❌ Invalid Variable Names

```csharp
int 1age;
```

Reason

Starts with a number.

---

```csharp
int student age;
```

Reason

Contains space.

---

```csharp
int class;
```

Reason

`class` is a C# keyword.

---

```csharp
int total@Marks;
```

Reason

Contains special character.

---

# Variable Naming Conventions

Just because something **works** doesn't mean it's **good code**.

Professional developers follow Microsoft's naming conventions.

| Bad | Good |
|------|------|
| a | age |
| n | studentName |
| x | totalMarks |
| abc | averageSalary |
| d | joiningDate |

---

## Use PascalCase?

```
StudentName
```

Used for

- Class Names
- Method Names
- Property Names

Example

```csharp
class Student
{
}
```

---

## Use camelCase?

```
studentName
```

Used for

Variables.

```csharp
string studentName;
```

This is Microsoft's recommended style.

---

# Should Variable Names Be Short?

Consider this.

```csharp
int a;
```

Will it work?

✅ Yes

Will someone understand it after six months?

❌ Probably not.

Now compare.

```csharp
int employeeSalary;
```

Immediately understandable.

Good variable names reduce bugs.

---

# Memory Diagram

Suppose we write

```csharp
string name = "Rahul";
int age = 25;
double marks = 91.8;
bool passed = true;
```

Conceptually, memory looks like this:

```
RAM

+-----------------------------+
| name    | "Rahul"          |
+-----------------------------+

+-----------------------------+
| age     | 25               |
+-----------------------------+

+-----------------------------+
| marks   | 91.8             |
+-----------------------------+

+-----------------------------+
| passed  | true             |
+-----------------------------+
```

> **Note**
>
> This is a simplified illustration to help you understand the idea of variables.
> The actual memory layout used by the CLR is more complex.

---

# Example 1 — Basic

```csharp
using System;

class Program
{
    static void Main()
    {
        string name = "Rahul";
        int age = 25;

        Console.WriteLine(name);
        Console.WriteLine(age);
    }
}
```

Output

```
Rahul
25
```

---

# Example 2 — Intermediate

```csharp
using System;

class Program
{
    static void Main()
    {
        string studentName = "Rahul";
        int rollNumber = 101;
        double percentage = 91.5;
        bool passed = true;

        Console.WriteLine(studentName);
        Console.WriteLine(rollNumber);
        Console.WriteLine(percentage);
        Console.WriteLine(passed);
    }
}
```

Output

```
Rahul
101
91.5
True
```

Notice how each variable stores a different type of information.

---

# Example 3 — Professional Example

Imagine you're building a **Student Management System**.

```csharp
using System;

class Program
{
    static void Main()
    {
        int studentId = 1001;
        string studentName = "Rahul";
        byte age = 21;
        decimal courseFee = 45000m;
        double attendance = 92.75;
        bool feePaid = true;

        Console.WriteLine($"ID          : {studentId}");
        Console.WriteLine($"Name        : {studentName}");
        Console.WriteLine($"Age         : {age}");
        Console.WriteLine($"Course Fee  : {courseFee}");
        Console.WriteLine($"Attendance  : {attendance}%");
        Console.WriteLine($"Fee Paid    : {feePaid}");
    }
}
```

### Why were these data types chosen?

| Variable | Data Type | Reason |
|-----------|-----------|--------|
| studentId | int | Plenty of range |
| studentName | string | Text |
| age | byte | Human age fits easily |
| courseFee | decimal | Financial value |
| attendance | double | Decimal percentage |
| feePaid | bool | Only true or false |

---

# What Happens If...

## Using int for Name

```csharp
int name = "Rahul";
```

❌ Compile-time error.

Reason

An `int` can store only whole numbers.

---

## Using string for Salary

```csharp
string salary = "50000";
```

Works?

✅ Yes

Can we calculate?

```csharp
salary + 1000
```

No.

The result becomes

```
500001000
```

because strings are joined together.

Correct approach

```csharp
decimal salary = 50000m;
```

---

## Forgetting to Initialize

```csharp
int marks;

marks += 10;
```

❌ Compile-time error.

Reason

The compiler doesn't know the starting value.

Initialize first.

```csharp
int marks = 0;

marks += 10;
```

---

## Assigning Wrong Type

```csharp
double percentage = true;
```

❌ Compile-time error.

Every data type accepts only compatible values.

---

## Storing Large Number in byte

```csharp
byte number = 300;
```

❌ Compile-time error.

Reason

Maximum value of `byte`

```
255
```

Choose

```csharp
int
```

instead.

---

# Best Practices

✅ Use meaningful variable names.

```csharp
double averageMarks;
```

Better than

```csharp
double x;
```

---

✅ Initialize variables whenever possible.

---

✅ Use `int` for most whole numbers.

---

✅ Use `decimal` for money.

---

✅ Use `bool` for Yes/No information.

---

✅ Use `string` for text.

---

✅ Keep variable scope as small as possible.

Declare variables only where they are needed.

---

# Common Beginner Mistakes

| Mistake | Better Approach |
|----------|-----------------|
| `int Name` | `string name` |
| `float salary` | `decimal salary` |
| `string age = "25"` | `int age = 25` |
| `int x` | `int studentAge` |
| Using `long` everywhere | Use `int` unless required |
| Forgetting initialization | Initialize before use |

---

# Interview Corner

### Q1. What is a variable?

A named storage location that stores data.

---

### Q2. What is a data type?

A data type specifies what kind of data can be stored and how much memory it requires.

---

### Q3. Difference between declaration and initialization?

Declaration creates the variable.

Initialization gives it its first value.

---

### Q4. Why is `decimal` preferred for money?

Because it provides high decimal precision and avoids floating-point rounding errors.

---

### Q5. Difference between `char` and `string`?

`char`

Stores exactly one character.

Example

```csharp
'A'
```

`string`

Stores multiple characters.

Example

```csharp
"Apple"
```

---

### Q6. Does `var` mean dynamically typed?

No.

The compiler infers the type at compile time.

---

### Q7. Why does C# require initialization of local variables?

To prevent unpredictable behavior caused by reading undefined values.

---

# Think Like a Developer

Writing code that **works** is good.

Writing code that is **correct, maintainable, readable, and efficient** is what makes you a professional developer.

Whenever you declare a variable, ask yourself these questions.

---

# Decision Tree – Which Data Type Should I Use?

```
Need to Store Data
        │
        ▼
What kind of data?
        │
        ├──────────────► Whole Number?
        │                     │
        │                     ▼
        │             Within ±2 Billion?
        │                     │
        │             ┌───────┴────────┐
        │             │                │
        │            Yes              No
        │             │                │
        │             ▼                ▼
        │            int             long
        │
        ├──────────────► Decimal Number?
        │                     │
        │                     ▼
        │                 Money?
        │                     │
        │             ┌───────┴────────┐
        │             │                │
        │            Yes              No
        │             │                │
        │             ▼                ▼
        │         decimal          double
        │
        ├──────────────► Text?
        │                     │
        │                     ▼
        │          One Character?
        │             │
        │      ┌──────┴──────┐
        │      │             │
        │     Yes           No
        │      │             │
        │      ▼             ▼
        │     char        string
        │
        └──────────────► Yes / No ?
                              │
                              ▼
                             bool
```

---

# Think Before Choosing a Data Type

## Should I use `int` or `long`?

Use **int** if:

- Age
- Roll Number
- Employee ID
- Quantity
- Marks
- Population of a city

Use **long** if:

- Aadhaar-like large IDs
- Nanoseconds
- File sizes
- Very large counters

### Professional Rule

> **Start with `int`. Upgrade to `long` only when necessary.**

---

## Should I use `float`, `double`, or `decimal`?

| Situation | Best Choice |
|------------|-------------|
| Money | decimal |
| Scientific calculations | double |
| Graphics/Game development | float |
| General decimal values | double |

---

## Should I use `char` or `string`?

Need exactly one character?

```
'A'
'B'
'9'
'?'
```

Use

```csharp
char
```

Need multiple characters?

```
"Rahul"

"Physics"

"Hello"
```

Use

```csharp
string
```

---

## Should I use `var`?

Good example

```csharp
var studentName = "Rahul";
```

The type is obvious.

Not recommended

```csharp
var x = GetData();
```

Without knowing what `GetData()` returns, the type isn't obvious.

### Professional Rule

Use `var` only when it improves readability.

---

# Why Did Microsoft Design C# This Way?

Many beginners ask:

> "Why can't C# automatically convert everything?"

Because automatic conversions can introduce bugs.

Example

Suppose this were allowed:

```csharp
bool passed = 1;
```

Now imagine

```csharp
bool passed = 2;
```

What should happen?

Should it mean

```
true
```

or

```
false
```

Different languages made different choices.

C# avoids this confusion by requiring explicit, type-safe code.

---

# Why Doesn't C# Guess the Data Type?

Suppose you write

```csharp
age = 25;
```

The compiler has several unanswered questions.

```
Should age be

byte?

short?

int?

long?

double?

decimal?

object?
```

Since it cannot safely guess, C# requires you to specify the type (or use `var` with an initializer).

This makes programs predictable and easier to maintain.

---

# Why Can't One Variable Store Every Type?

Imagine this.

```csharp
int age = 25;

age = "Rahul";
```

Should this be allowed?

If yes,

how many bytes should the compiler reserve?

```
4?

8?

100?

1000?
```

The compiler would no longer know what the variable represents.

By fixing the type, C# prevents accidental misuse.

---

# Why Does C# Care About Data Types?

Data types provide:

- Type Safety
- Better Performance
- Predictable Memory Usage
- Compile-Time Error Detection
- Easier Code Maintenance

Without data types,

programs would be slower, less reliable, and harder to debug.

---

# Common "What Happens If...?" Questions

---

## What happens if I assign a decimal to an int?

```csharp
int number = 10.5;
```

❌ Compile-time error.

Reason

An `int` stores whole numbers only.

Correct

```csharp
double number = 10.5;
```

---

## What happens if I assign a huge number to int?

```csharp
int number = 999999999999;
```

❌ Compile-time error.

Reason

The value exceeds the range of `int`.

Choose

```csharp
long
```

instead.

---

## What happens if I use decimal everywhere?

Works?

✅ Yes

Recommended?

Usually ❌ No.

Reason

- Uses more memory
- Slower than `double`
- Unnecessary unless exact decimal precision is required

Choose the smallest suitable type.

---

## What happens if I never change a value?

Example

```csharp
double PI = 3.1415926535;
```

This works.

But suppose someone accidentally writes

```csharp
PI = 4;
```

Now every calculation using PI becomes incorrect.

Better

```csharp
const double PI = 3.1415926535;
```

We'll learn `const` in detail later.

---

## What happens if I choose meaningless names?

```csharp
int a;
int b;
int c;
```

Works?

✅ Yes

Understandable after six months?

❌ Probably not.

Better

```csharp
int studentAge;
decimal courseFee;
double averageMarks;
```

Readable code saves debugging time.

---

# Variable Selection Cheat Sheet

| Need | Choose |
|--------|---------|
| Whole Number | int |
| Very Large Number | long |
| Decimal | double |
| Money | decimal |
| Single Character | char |
| Text | string |
| Yes/No | bool |
| Type Obvious | var |

---

# Quick Revision

## Variable

```
Named Memory Location
```

---

## Data Type

```
Defines

• Type of Data

• Memory Required

• Allowed Operations
```

---

## Declaration

```csharp
int age;
```

---

## Initialization

```csharp
int age = 25;
```

---

## Assignment

```csharp
age = 30;
```

---

## Most Common Types

```
int

double

decimal

string

char

bool
```

---

# Mini Quiz

## Question 1

Which data type should store a student's name?

A. int

B. string

C. bool

D. char

**Answer:** B

---

## Question 2

Which data type is best for money?

A. float

B. double

C. decimal

D. long

**Answer:** C

---

## Question 3

Which keyword lets the compiler infer the type?

A. auto

B. dynamic

C. var

D. infer

**Answer:** C

---

## Question 4

Which declaration is correct?

A.

```csharp
int age = "25";
```

B.

```csharp
string age = 25;
```

C.

```csharp
int age = 25;
```

D.

```csharp
bool age = 25;
```

**Answer:** C

---

## Question 5

What is the purpose of a data type?

A. To print values

B. To define the kind of data and memory required

C. To make variables faster

D. To create methods

**Answer:** B

---

# Summary

In this chapter, you learned:

- ✔ What a variable is
- ✔ Why variables exist
- ✔ What data types are
- ✔ Variable declaration, initialization, and assignment
- ✔ Classification of variables
- ✔ Classification of data types
- ✔ Numeric, text, and Boolean types
- ✔ The `var` keyword
- ✔ Naming rules and conventions
- ✔ Common mistakes
- ✔ Best practices
- ✔ Practical examples
- ✔ Decision guides
- ✔ What happens when you choose the wrong type

You now have the foundation required to write meaningful C# programs.

---

# What's Next?

Variables allow us to **store data**.

The next question is:

> **How do we perform calculations or comparisons using that data?**

For example:

```csharp
int a = 10;
int b = 20;
```

How do we:

- Add them?
- Subtract them?
- Compare them?
- Check if they are equal?
- Combine conditions?

These operations are performed using **Operators**.

➡ **Next Chapter:** **Theory - Operators.md**

---

## Chapter Completion Checklist

Before moving to the next chapter, ensure you can confidently answer **Yes** to the following:

- [ ] I know what a variable is.
- [ ] I understand why variables exist.
- [ ] I can declare and initialize variables.
- [ ] I can choose the correct data type.
- [ ] I know when to use `int`, `double`, `decimal`, `char`, `string`, and `bool`.
- [ ] I understand the difference between declaration, initialization, and assignment.
- [ ] I can follow C# naming conventions.
- [ ] I understand common mistakes and how to avoid them.

---

**End of Chapter 1 – Variables and Data Types**