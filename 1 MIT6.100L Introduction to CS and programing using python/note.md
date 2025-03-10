# MIT6.100L 
## Lecture 1 Introduction
### SCALAR OBJECTS
- int-represent integers,ex.5，-100
- float-represent real numbers,ex.3.27，2.0
- bool -represent Boolean values True and False
- NoneType -special and has one value, None
- Can use type() to see the type of an object

### TYPE CONVERSIONS(CASTING)
- Can convert object of one type to another
    - float(3) casts the int 3 to float 3.0
    - int(3.9) casts (note the truncation!取整) the float 3.9 to int 3
- Some operations perform implicit隐式 casts
    - round(3.9)四舍五入 returns the int 4

### EXPRESSIONS
- Combine objects and operators to form expressions
- An expression has a value, which has a type
    - 3+2 has value 5 and type int
    - 5/3 has value 1.666667 and type float
- Python evaluates expressions and stores the value. lt doesn'tstore expressions!
- Syntax for a simple expression
< object >< operator >
< object >

### OPERATORS on int and float
- i//j floor division 向下取整
- i%j the remainder when i is divided by j
- i**j i to the power of j

### SIMPLE OPERATIONS
- () tell python to do these operations first
- operator precedence优先级 without parentheses括号
    - **
    -  / % * executed left to right, as appear in expression
    -  "- +" executed left to right, as appear in expression

### VARIABLES
- Computer science variables are different than math variables
- Math variables
    - Abstract
    - Can represent many values
- CS variables
    - Is bound to one single value at a given time
    - Can be bound to an expression(but expressions evaluate to one value!)

### BINDING VARIABLES tO VALUES
- In CS, the equal sign is an assignment
    - "One value to one variable name
    - Equal sign is not equality, not “solve for x”
- An assignment binds a value to a name
> pi=355/113
- Step 1: Compute the value on the right hand side (the VALUE)
    - "Value stored in computer memory
- Step 2: Store it (bind it) to the left hand side (the VARIABLE)
    - "Retrieve value associated with name by invoking the name(typing it out)

## Lecture 2

### Slicing to get one character in a string 
- s="abc"
- s[0]="a"
- s[1]="b"
- s[2]="c"
- s[-1]="c"
- s[-2]="b"
- s[-3]="a"

### Slicing to get a  substring
- Can slice string using [start:stop:step]
- Get character at start, up to and including stop-1, taking every step character
- s="sbcdefgh"
- s[3:6]="def"
- s[3:6:2]="df"
- s[:]="sbcdefgh"， same as s[0:len(s):1]
- s[::-1]="hgfedcba"

### IMMUTABLE不可变的 STRINGS
- Strings are “immutable”-cannot be modified
- You can create new objects that are versions of the original one
- Variable name can only be bound to one object
- S = "car"
- s[0]= 'b'
    - gives an error
- s ='b'+s[1:len(s)]
    - is allowed,s bound to new object

### printing
- print()
- a="the"
- b=3
- c="musketeers"
- print(a,b,c)
    - the 3 musketeers
- print(a+b+c)
    - this is an error
- print(a+str(b)+c)
    - the3musketeers

### input
- x = input(s)
    - "Prints the value of the string s
    - User types in something and hits enter
    - That value is assigned to the variable x
- Binds that value to a variable
    - text = input("Type anything:")
    - print(5*text)
- input always returns an str, must cast if working with numbers

### logical operators on bool
- not 
- and
- or

### branching in python
    if<condition>:
        <code>
        <code>

    if<condition>:
        <code>
        <code>
    else:
        <code>
        <code>

    if<condition>:
        <code>
        <code>
    elif<condition>:
        <code>
        <code>
    elif<condition>:
        <code>
        <code>

## Lecture 3 Iteration

### Control flow: while loop
    while <condition>:
        <code>
        <code>
### structure of for loops
    for <variable> in <sequence of values>:
        <code>
        ...
- each time through the loop, < variable > takes a value
- First time ,< variable > is the first value in sequence
- Next time, < variable > gets the second value

### A common sequence of values
    for <variable> in range <some_num>:
        <code>
        ...

- range<some_num> means 0-some_num-1

### range
- Generates a sequence of ints, following a pattern 
- range(start, stop,step)
    - start: first int generated
    - stop: controls last int generated (go up to but not including this int)
    - step: used to generate next int in sequence

## Lecture 4 Loops over strings, guess-and-check, binary

### break statement
- Immediately exits whatever loop it is in 
- Skips remaining expression in code block
- **Exits only innermost loop**

### Guess-and-check
- Process called exhaustive enumeration 穷举法
- Applies to problem where ...
    - You are able to guess a value for solution
    - You are able to check if the solution is correct 
- You are keep guessing until
    - Find solution or
    - Have guessed all values

### Guess-and-check root
- Basic idea
    - Given an int, call it x, want to see if there is another int which is its square root
    - Start with a guess and check if it is the right answer

### Operations on some floats introduces a very small error
The small error can have a big effect if operations are done many times.

### FLOATING POINT REPRESENTATION
- Depends on computer hardware, not programming language implementation
- Key things to understand
    - Numbers (and everything else) are represented as a sequence of bits (0 or 1).
    - When we write numbers down, the notation uses base 10.
        - 0.1 stands for the rational number 1/10
    - This produces cognitive dissonance - and it will influence how we write code


## Lecture 5 Floats and Approximation Methods

### Fractions
- what does the decimal fraction 0.abc mean
    - a\*10^-1 + b\*10^-2 + c\*10^-3
- For binary representation, we use the same idea
    - a\*2^-1 + b\*2^-2 + c\*2^-3
- Or to put this in simpler terms, the binary representation of a decimal fraction f would require finding the values of a, b, c, etc. such that
    - f=0.5a+0.25b+0.125c+0.0625d+0.03125e... 
- In decimal form:3/8=0.375=3\*10^-1 + 7\*10^-2+5\*10^-3
- Recipe idea: if we can multiply by a power of 2 big enough to turn into a whole number, can convert to binary, and then divide by the same power of 2 to restore
    - 0.375*(2**3)=3
    - Convert 3 to binary (now 11)
    - Divide by 2**3 (shift right three spots) to get 0.011

### Storing floating point numbers
- Floating point is a pair of integers
    - Significant digits and base 2 exponent指数
    - (1,1) - 1\*2^1 - 10 - 2.0
    - (1,-1) - 1\*2^-1 - 0.1 - 0.5
    - (125,-2) - 125\*2^-2 - 11111.01 - 31.25

### USE A FINITE SET OF BITS TO REPRESENT A POTENTIALLY INFINITE SET OF BITS
- The maximum number of significant digits governs the precision with which numbers can be represented
- Most modern computers use 32 bits to represent significant digits
- lf a number is represented with more than 32 bits in binary, the number will be rounded
    - Error will be at the 32nd bit
    - Error will only be on order of 2\*10^-10

### Summary 
- Floating point numbers introduce challenges!
- They can't be represented in memory exactly
    - Operations on floats introduce tiny errors
    - "Multiple operations on floats magnify errors
- Approximation methods use floats
    - Like guess-and-check except that
        - We use a float as an increment
        - We stop when we are close enough
    - Never use == to compare floats in the stopping condition
    - Be careful about overshooting the close-enough stopping condition

## Lecture 6 Bisection Search 二分查找

### Log growth is better
- The brute force method is **linear in size of problem**
- Bisection search is **logarithmic in size of problem**

### Some observation
- Bisection search **radically reduces computation time** - being smart about generating guesses is important
- Search space gets **smaller quickly at begining** and then more slowly (in absolute terms, but not as a fraction of search space) later
- Works on **problems with "ordering" property**

### Iterative algorithms
- Guess and check methods build on **reusing same code**
    - Use a looping construct
    - Generate guesses
    - Check and continue
- **Generating guesses**
    - Exhaustive enumeration穷举法
    - Approximation algorithm 近似法
    - Bisection search 二分查找
    - Newton-Raphson(for root finding)

### DECOMPOSITION and ABSTRACTION
- Decomposition:
    - ldeally parts can be reused by other programs
    - Self-contained means parts should **complete computation using only inputs provided** to them and "basic" operations
- Abstraction:
    - Used to separate what something does, from how it actually does it
    - Creating parts and abstracting away details allows us to write complex code while suppressing details, so that we are not overwhelmed by that complexity.

## Lecture 7 Decomposition, Abstraction, and Functions