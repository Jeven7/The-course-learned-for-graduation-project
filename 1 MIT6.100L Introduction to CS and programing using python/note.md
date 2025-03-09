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
