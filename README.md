# Values and types

Values and types

A value is one of the basic things a program works with, like a letter or a number. 
These values belong to different types: 2 is an integer, and “Hello, World!” is a
string, so called because it contains a “string” of letters. You (and the interpreter)
can identify strings because they are enclosed in quotation marks.

If you are not sure what type a value has, the interpreter can tell you.
>>> type('Hello, World!')

<class 'str'>

>>> type(17)

<class 'int'>

Strings belong to the type str and integers belong to the type
int. Numbers with a decimal point belong to a type called float,
because these numbers are represented in a format called floating point.
>>> type(3.2)

<class 'float'>

Values like “17” and “3.2”? They look like numbers, but they are in
quotation marks like strings.

>>> type('17')

<class 'str'>

>>> type('3.2')

<class 'str'>

They’re strings.

# Variables

One of the most powerful features of a programming language is the ability to
manipulate variables. A variable is a name that refers to a value. An assignment statement creates new variables and gives them values:

>>> message = 'And now for something completely different'

>>> n = 17

>>> pi = 3.1415926535897931

This example makes three assignments.

The first assigns a string to a new variable
named message; the second assigns the integer 17 to n; the third assigns the
(approximate) value of π to pi.


To display the value of a variable, you can use a print statement:
>>> print(n)

17

>>> print(pi)

3.141592653589793


The type of a variable is the type of the value it refers to.

>>> type(message)

<class 'str'>

>>> type(n)

<class 'int'>

>>> type(pi)

<class 'float'>


# Variable names and keywords

Programmers generally choose names for their variables that are meaningful and
document what the variable is used for.

Variable names can be arbitrarily long. They can contain both letters and numbers,
but they cannot start with a number. 
It is legal to use uppercase letters, but it is a good idea to begin variable names with a lowercase letter.
The underscore character ( _ ) can appear in a name. It is often used in names with
multiple words, such as my_name or airspeed_of_unladen_swallow. Variable names can start with an underscore character, but we generally avoid doing this unless we are writing library code for others to use.


If you give a variable an illegal name, you get a syntax error:

>>> 76trombones = 'big parade'

SyntaxError: invalid syntax

>>> more@ = 1000000

SyntaxError: invalid syntax

>>> class = 'Advanced Theoretical Zymurgy'

SyntaxError: invalid syntax

76trombones is illegal because it begins with a number. 
more@ is illegal because it contains an illegal character, @. But what’s wrong with class?

It turns out that class is one of Python’s keywords. The interpreter uses keywords
to recognize the structure of the program, and they cannot be used as variable
names.

Python reserves 35 keywords:

and del from None True
as elif global nonlocal try
assert else if not while
break except import or with
class False in pass yield
continue finally is raise async
def for lambda return await

# Statements
A statement is a unit of code that the Python interpreter can execute. We have
seen two kinds of statements: print being an expression statement and assignment.
When you type a statement in interactive mode, the interpreter executes it and
displays the result, if there is one.

A script usually contains a sequence of statements. If there is more than one
statement, the results appear one at a time as the statements execute.

For example, the script

>>>print(1)

>>>x = 2

>>>print(x)

produces the output

1

2

The assignment statement produces no output.


# Operators and operands
Operators are special symbols that represent computations like addition and multiplication.
The values the operator is applied to are called operands.

The operators +, -, *, /, and ** perform addition, subtraction, multiplication,
division, and exponentiation, as in the following examples:

20+32

hour-1

hour*60+minute

minute/60

5**2

(5+9)*(15-7)

There has been a change in the division operator between Python 2.x and Python
3.x. In Python 3.x, the result of this division is a floating point result:

>>> minute = 59

>>> minute/60
>>> 
0.9833333333333333
1.
The division operator in Python 2.0 would divide two integers and truncate the
result to an integer:

>>> minute = 59

>>> minute/60

0

To obtain the same answer in Python 3.0 use floored ( // integer) division.

>>> minute = 59

>>> minute//60

0

# Expressions

An expression is a combination of values, variables, and operators. A value all by
itself is considered an expression, and so is a variable, so the following are all legal
expressions (assuming that the variable x has been assigned a value):

17

x

x + 17

If you type an expression in interactive mode, the interpreter evaluates it and
displays the result:

>>> 1 + 1

2

But in a script, an expression all by itself doesn’t do anything! This is a common
source of confusion for beginners.

# Order of operations

When more than one operator appears in an expression, the order of evaluation
depends on the rules of precedence. For mathematical operators, Python follows
mathematical convention. The acronym PEMDAS is a useful way to remember
the rules:

• Parentheses have the highest precedence and can be used to force an expression
to evaluate in the order you want. Since expressions in parentheses are
evaluated first, 2 * (3-1) is 4, and (1+1)**(5-2) is 8. You can also use
parentheses to make an expression easier to read, as in (minute * 100) /
60, even if it doesn’t change the result.

• Exponentiation has the next highest precedence, so 2**1+1 is 3, not 4, and
3*1**3 is 3, not 27.

• Multiplication and Division have the same precedence, which is higher than
Addition and Subtraction, which also have the same precedence. So 2*3-1
is 5, not 4, and 6+4/2 is 8, not 5.

• Operators with the same precedence are evaluated from left to right. So the
expression 5-3-1 is 1, not 3, because the 5-3 happens first and then 1 is
subtracted from 2.

# Modulus operator

The modulus operator works on integers and yields the remainder when the first
operand is divided by the second. In Python, the modulus operator is a percent
sign (%). The syntax is the same as for other operators:

>>> quotient = 7 // 3

>>> print(quotient)

2

>>> remainder = 7 % 3

>>> print(remainder)

1

So 7 divided by 3 is 2 with 1 left over.

The modulus operator turns out to be surprisingly useful. For example, you can
check whether one number is divisible by another: if x % y is zero, then x is
divisible by y.

You can also extract the right-most digit or digits from a number. For example,
x % 10 yields the right-most digit of x (in base 10). Similarly, x % 100 yields the
last two digits.


# String operations

The + operator works with strings, but it is not addition in the mathematical sense.
Instead it performs concatenation, which means joining the strings by linking them
end to end. For example:

>>> first = 10

>>> second = 15

>>> print(first+second)

25

>>> first = '100'

>>> second = '150'

>>> print(first + second)

100150

The * operator also works with strings by multiplying the content of a string by
an integer. For example:

>>> first = 'Test '

>>> second = 3

>>> print(first * second)

Test Test Test

# Asking the user for input

Sometimes we would like to take the value for a variable from the user via their
keyboard. Python provides a built-in function called input that gets input from
the keyboard1. When this function is called, the program stops and waits for the
user to type something. When the user presses Return or Enter, the program
resumes and input returns what the user typed as a string.

>>> inp = input()

Some silly stuff

>>> print(inp)

Some silly stuff

Before getting input from the user, it is a good idea to print a prompt telling the
user what to input. 
You can pass a string to input to be displayed to the user
before pausing for input:

>>> name = input('What is your name?\n')

What is your name?

Chuck

>>> print(name)

Chuck

The sequence \n at the end of the prompt represents a newline, which is a special
character that causes a line break. That’s why the user’s input appears below the
prompt.

If you expect the user to type an integer, you can try to convert the return value
to int using the int() function:

>>> prompt = 'What...is the airspeed velocity of an unladen swallow?\n'

>>> speed = input(prompt)

What...is the airspeed velocity of an unladen swallow?

17

>>> int(speed)

17

>>> int(speed) + 5

22

But if the user types something other than a string of digits, you get an error:

>>> speed = input(prompt)

What...is the airspeed velocity of an unladen swallow?

What do you mean, an African or a European swallow?

>>> int(speed)

ValueError: invalid literal for int() with base 10:

# Comments
As programs get bigger and more complicated, they get more difficult to read.
Formal languages are dense, and it is often difficult to look at a piece of code and
figure out what it is doing, or why.

For this reason, it is a good idea to add notes to your programs to explain in
natural language what the program is doing. These notes are called comments,
and in Python they start with the # symbol:

#compute the percentage of the hour that has elapsed

percentage = (minute * 100) / 60

In this case, the comment appears on a line by itself. You can also put comments
at the end of a line:

percentage = (minute * 100) / 60 # percentage of an hour

Everything from the # to the end of the line is ignored; it has no effect on the
program.

Comments are most useful when they document non-obvious features of the code.
It is reasonable to assume that the reader can figure out what the code does; it is
much more useful to explain why.

This comment is redundant with the code and useless:

v = 5 # assign 5 to v

This comment contains useful information that is not in the code:

v = 5 # velocity in meters/second.

Good variable names can reduce the need for comments, but long names can make
complex expressions hard to read, so there is a trade-off.

# Debugging
At this point, the syntax error you are most likely to make is an illegal variable
name, like class and yield, which are keywords, or odd~job and US$, which
contain illegal characters.

If you put a space in a variable name, Python thinks it is two operands without
an operator:

>>> bad name = 5

SyntaxError: invalid syntax

>>> month = 09

  File "<stdin>", line 1
  month = 09
           ^
  
SyntaxError: invalid token

For syntax errors, the error messages don’t help much. The most common messages
are SyntaxError: invalid syntax and SyntaxError: invalid token, neither
of which is very informative.
  
The runtime error you are most likely to make is a “use before def;” that is, trying
to use a variable before you have assigned a value. This can happen if you spell a
variable name wrong:
  
>>> principal = 327.68
  
>>> interest = principle * rate
  
NameError: name 'principle' is not defined
  
Variables names are case sensitive, so LaTeX is not the same as latex.
  
At this point, the most likely cause of a semantic error is the order of operations.
  
For example, to evaluate 1/2π, you might be tempted to write
  
>>> 1.0 / 2.0 * pi
  
But the division happens first, so you would get π/2, which is not the same thing!
There is no way for Python to know what you meant to write, so in this case you
don’t get an error message; you just get the wrong answer.





