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

### Suppress details with abstraction
- Coder achives abstraction with a **function (or procedure)**
- A function lets us capture code within a black box
    - Once we create function, it will produce an output from inputs, while hiding details of how it does the computation
- A function has **specifications**, captured using **docstrings**

### Create structure with decomposition
- Given the idea of black box straction, use it to **divide code into modules** that are:
    - **Self-contained**
    - Intended to be reusable
- Modules are used to:
    - **Break up** code into logical pieces
    - Keep code **organized**
    - Keep code **coherent** (readable and understandable)
- Decomposition relies on abstraction to enable construction of complex modules from simpler ones

### Functions
- Reusable pieces of code called **functions** or **procedures**
- A function is just some **code written in a special, reusable way**

### FUNCTION CHARACTERISTICS
- Has a name
    - (think: variable bound to a function object)
- Has (formal) parameters (0 or more)
    - The inputs
- Has a docstring (optional but recommended)
    - A comment delineated by " "" (triple quotes) that provides a specification for the function-contract relating output to input
- Has a body, a set of instructions to execute when function is called
- Returns something
    - Keyword return

## Lecture 8 Functions as Objects
### Understanding function calls
- It **creates a new environment** with every function call
    - Like a **mini program** that it needs to complete
    - This mini program runs with **assigning its parameters** to some inputs
    - It does the work (aka the **body** of the function)
    - It **returns** the value
    - The **environment disappears** after it returns the value

### Variable scope
- **Formal parameters** get bound to the value of **input parameters**
- **Scope** is mapping of names to objects
    - Defines context in which body is evaluated
    - Values of variables given by bindings of names
- Expressions in body of function evaluated wrt this new scope

### HIGHER ORDER PROCEDURES
- Objects in Python have a type
    - int, float, str, Boolean, NoneType, function
- Objects can appear in RHS of assignment statement
    - Bind a name to an object
- Objects
    - Can be **used as an argument** to a procedure
    - Can be **returned as a value** from a procedure
- Functions are also first class objects!
- Treat functions just like the other types
    - Functions can be arguments to another function
    - Functions can be returned by another function

## Lecture 9 Lambda functions, tuples and lists
### Anonymous匿名  functions
- Sometimes don't want to name functions, especially simple ones.
- Can use an anonymous procedure by using lambda
    `` lambda x: x%2==0``
- lambda creates a procedure/function object, but simply does not bind a name to it
- Function call with a named function: 
    `` apply(is_even,10)``
- Function call with an anonymous functions as parameter: 
    ``apply(lambda x: x%2==0,10)``
- lambda function is **one-time use**. It can't be reused because it has no name

### A new data type
- Want to introduce more general compound data types
    - Indexed sequences of elements, which could themselves be compound structures
    - Tuples-immutable不可变
    - Lists-mutable可变

### Tuples
- Indexable ordered sequence of objects
    - Objects can be any type -int, string, tuple, tuple of tuples, ...
- Cannot change element values,immutable

code:

    te =() # Empty tuple
    ts =(2，) #Extra comma means tuple with one element

    t=(2，"mit"，3)
    t[0]  #evaluates to 2
    (2,"mit",3)+(5,6)  # evaluates to anew tuple(2,"mit",3,5,6)
    t[1:2]   #slice tuple, evaluates to("mit",)
    t[1:3]  #slice tuple, evaluates to("mit",3)
    len(t)  #evaluates to 3
    max((3,5,0))  #evaluates 5
    t[1]= 4   #gives error, can't modify object
- convebniently used to **swap** variable values
#

    x=1
    y=2
    (x,y)=(y,x)
- used to **return more than one value** from a function

### VARIABLE NUMBER Of ARGUMENTS
- Python has some built-in functions that take variable number of arguments, e.g, min
- Python allows a programmer to have same capability, using **\* notation**
- numbers is bound to a **tuple of the supplied values**
#
    def mean(*args):
        tot =0
        for a in args:
            tot += a
        return tot/len(args)

- Example:
    - mean(1,2,3,4,5,6)

### LISTS
- Indexable ordered sequence of objects
    - Usually homogeneous同构 (i.e., all integers, all strings, all lists)
    - But can contain mixed types (not common)
- Denoted by square brackets, []
- Mutable, this means you can change values of specific
elements of list


## Lecture 10 Lists and mutability
### Mutability
- Lists are mutable
- Assigning to an element at an index changes the value

### Operation on lists - append
- Add an element to end of list with `L.append(element)`
- Mutates the list

### Strings to lists
- Convert string to list with `list(s)`
    - Every character from s is an element in a list
- Use `s.split()`, to **split a string on a character** paramete, splits on spaces if called without a parameter

### Lists to strings
- Convert a **list of strings back to string**
- Use `''.join(L)` to turn **a list of strings into a bigger string**
- Can give a character in quotes to add char between every element 

### A FEW INTERESTING LIST OPERATIONS
- `sort()`
    - L=[4,2,7]
    - L.sort()
    - Mutates L
- `reverse()`
    - L=[4,2,7]
    - L.reverse()
    - Mutates L
- `sorted()`
    - L=[4,2,7]
    - L_new=sorted(L)
    - Returns a sorted version of L(no mutation!)

### Combining lists
- Concatenation, + operator, creates a new list, with copies
- Mutate list with `L.extend(some_list)`(copy of some_list)

### Empty out a list and checking that it's the same object
- You can **mutate a list to remove all its elements**
    - This **does not make a new empty list**
- Use `L.clear()`
- How to check that it's **the same object in memory**?
    - use the `id()` function


## Lecture 11 Aliasing and cloning
### Making a copy of this list
- Can **make a copy of a list object** by duplicating all elements (top-level) into a new list object
- `Lcopy=L[:]`
    - Equivalent to looping over L and appending each element to Lcopy
    - This does not make a copy of elements that are lists (will see how to do this at the end of this lecture)

### OPERATION ON LISTS: remove
- Delete element at a **specific index** with `del(L[index])`
- Remove element at **end of list** with `L.pop ( )`,returns the removed element (can also call with specific index:`L.pop(3)`)
- Remove a **specific element** with `L.remove(element)`
    - Looks for the element and removes it (mutating the list)
    - lf element occurs multiple times, removes first occurrence
    - lfelement not in list, gives an error

### Aliasing
- All nicknames point to the same city
    - Add new attribute to one nickname
- All the aliased refer to the old attribute and all the new ones
- Assignment (= sign) on mutable object creates an **alias**, not a clone

### When you pass a list as a paramenter to a function, you are making an alias
- The **acture parameter** (from the function **call**) is an **alias** for the **formal parameter**(from the function **definition**)

### CONTROL COPYING
- Suppose we want to create a copy of a list, not just a sharedpointer
- Shallow copying does this at the top level of the list
    - Equivalent to syntax [:]
    - Any mutable elements are NOT copied
- Use this when your list contains immutable objects only
- lf we want all structures to be new copies, we need a deep copy
- Use deep copy when your list might have mutable elements to ensure every structure at every level is copied


## Lecture 12 List comprehension, functions as objects, testing and debugging

### LIST COMPREHENSIONS
- Applying a **function to every element of a sequence**, then
creating a new list with these values is a common concept
- Python provides a concise one-liner way to do this, called a **list
comprehension**
    - Creates a new list
    - Applies a function to every element of another iterable
    - Optional, only apply to elements that satisfy a test
`expression for ele in iterable if test`

### RULES for KEYWORD PARAMETERS
- In the **function definition**:
    - Default parameters must go at the end
- These are **ok for calling a function**:
    - `bisection_root_new(123)`
    - `bisection_root_new(123, 0.001)`
    - `bisection_root_new(123, epsilon=0.001)`
    - `bisection_root_new(x=123, epsilon=0.1)`
    - `bisection_root_new(epsilon=0.1, x=123)`
- These are **not ok for calling a function**:
    - `bisection_root_new(epsilon=0.001, 123) #error`
    - `bisection_root_new(0.001, 123) #no error but wrong`

### FUNCTIONS CAN RETURN FUNCTIONS
    def make_prod(a):
        def g(b):
            return a*b
        return g #This is not a function call
    
    val=make_prod(2)(3)
    print(val)

    doubler=make_prod(2)
    val=doubler(3)
    print(val)

### WHY BOTHER RETURNING FUNCTIONS?
- Code can be **rewritten** without returning function objects
- Good software design
    - Embracing ideas of **decomposition, abstraction**
    - Another **tool** to structure code
- Interrupting execution
    - Example of **control flow**
    - A way to achieve **partial execution** and use result somewhere else before finishing the full evaluation

### CLASSES OF TESTS
- Unit testing单元测试
    - Validate each piece of program
    - **Testing each function** separately
- Regression testing回归测试
    - Add test for bugs as you find them
    - **Catch reintroduced** errors that were previously fixed
- Integration testing集成测试
    - Does **overall program** work?
    - Tend to rush to do this

### TESTING APPROACHES
- **Intuition** about natural boundaries to the problem
-  If no natural partitions, might do **random testing**
    - Probability that code is correct increases with more tests
    - Better options below
- **Black box testing**
    - Explore paths through specification
- **Glass box testing**
    - Explore paths through code

### BLACK BOX TESTING
- Designed without looking at the code
- Can be done by someone other than the implementer to avoid some implementer biases
- Testing can be reused if implementation changes
- Paths through specification
    - Build test cases in different natural space partitions
    - Also consider boundary conditions (empty lists, singleton list, large numbers, small numbers)

### GLASS BOX TESTING
- Use code directly to guide design of test cases
- Called path-complete if every potential path through code is tested at least once
-  What are some drawbacks of this type of testing?
    - Can go through loops arbitrarily many times
    - Missing paths

### DEBUGGING
- Tools
    - Built in to IDLE and Anaconda
    - Python Tutor
    - print statement
    - Use your brain, be systematic in your hunt

### ERROR MESSAGES – EASY
- Trying to access beyond the limits of a list
`test = [1,2,3] then test[4] #IndexError`
- Trying to convert an inappropriate type
`int(test)  #TypeError`
- Referencing a non-existent variable
`a #NameError`
- Mixing data types without appropriate coercion
`'3'/4 #TypeError`
- Forgetting to close parenthesis, quotation, etc.
`a = len([1,2,3]`
`print(a)   #SyntaxError`


## Lecture 13 Expections and assertions
### HANDLING EXCEPTIONS
- Typically, exception causes an error to occur and execution to stop
- Python code can provide handlers for exceptions
####
    try:
        # do some potentially
        # problematic code
    except:
        # do something to
        # handle the problem
- If expressions in try block all succeed
    - Evaluation continues with code after except block
- Exceptions raised by any statement in body of try are handled by the except statement
    - Execution continues with the body of the except statement
    - Then other expressions after that block of code

### OTHER BLOCKS ASSOCIATED WITH A TRY BLOCK
- `else:`
    - Body of this is executed when execution of associated try body **completes with no exceptions**
- `finally"`
    - Body of this is always executed after try, else and except clauses, even if they raised another error or executed a break, continue or return
    - Useful for clean-up code that should be run no matter what else happened (e.g. close a file)

### WHAT TO DO WITH EXCEPTIONS?
- Fail silently:
    - Substitute default values or just continue
    - Bad idea! user gets no warning
- Return an “error” value
    - Complicates code having to check for a special value
- Stop execution, signal error condition
    `raise ValueError ("something is wrong")`

### ASSERTIONS: DEFENSIVE PROGRAMMING TOOL
- Want to be sure that assumptions on state of computation are as
expected
- Use an assert statement to raise an AssertionError exception if assumptions not met
`assert <statement that should be true>, "message is not true"`
- An example of good defensive programming
    - Assertions don’t allow a programmer to control response to unexpected
    conditions
    - Ensure that execution halts whenever an expected condition is not met
    - Typically used to check inputs to functions, but can be used anywhere
    - Can be used to check outputs of a function to avoid propagating bad
    values
    - Can make it easier to locate a source of a bug

### ASSERTIONS vs. EXCEPTIONS
- Goal is to **spot bugs as soon as introduced** and make clear where they happened
- Exceptions provide a way of handling unexpected input
    - Use when you don’t need to halt program execution
    - Raise exceptions if users supplies bad data input
- Use **assertions**:
    - Enforce conditions on a “contract” between a coder and a user
    - As a **supplement** to testing
    - Check **types** of arguments or values
    - Check that **invariants** on data structures are met
    - Check **constraints** on return values
    - Check for **violations** of constraints on procedure (e.g. no duplicates in a list)

## Lecture 14 Dictionaries
### A PYTHON DICTIONARY
- Store **pairs of data** as an **entry**
    - key (any immutable object)
        - str, int, float, bool, tuple, etc
    - value (any data object)
        - Any above plus lists and other dicts!
`my_dict={} #empty dictionary`

### DICTIONARY LOOKUP
- Similar to indexing into a list
- Looks up the key
- Returns the value associated with the key
    -  If key isn’t found, get an error
- There is no simple expression to get a key back given some value
####
    grades = {'Ana':'B', 'Matt':'A', 'John':'B', 'Katy':'A'}
    grades['John']  #evaluates to 'B'
    grades['Grace']  #gives a KeyError

### DICTIONARY OPERATIONS
` grades = {'Ana':'B', 'Matt':'A', 'John':'B', 'Katy':'A'}`
- Add an entry
`grades['Grace'] = 'A'`
- Change entry
`grades['Grace'] = 'C'`
- Delete entry
`del(grades['Ana'])`
- Test if key in dictionary
####
    'John' in grades #returns True
    'Daniel' in grades #returns False
    'B' in grades #returns False
- Can iterate over dictionaries but assume there is no guaranteed order
- Get an **iterable that acts like a tuple of all keys**
`grades.keys() #returns dict_keys(['Ana', 'Matt', 'John', 'Katy'])`
`list(grades.keys()) #returns ['Ana', 'Matt', 'John', 'Katy']`
- Get an iterable that acts like **a tuple of all dict values**
`grades.values()  #returns dict_values(['B', 'A', 'B', 'A'])`
`list(grades.values()) #returns ['B', 'A', 'B', 'A']`
- Get an **iterable that acts like a tuple of all items**
`grades.items()   #returns dict_items([('Ana', 'B'), ('Matt', 'A'), ('John', 'B'), ('Katy', 'A')])`
`list(grades.items())   #returns [('Ana', 'B'), ('Matt', 'A'), ('John', 'B'), ('Katy', 'A')]`
- Typical use is to **iterate over key,value tuple**
#### 
    for k,v in grades.items():
        print(f"key {k} has value {v}")

### DICTIONARY KEYS & VALUES
- Dictionaries are mutable objects (aliasing/cloning rules apply)
    - Use = sign to make an alias
    - Use `d.copy()` to make a copy
- Assume there is no order to keys or values!
- Dict values
    - Any type (immutable and mutable)
        - Dictionary values can be lists, even other dictionaries!
    - Can be duplicates
- Keys
    - Must be unique
    - Immutable type (int, float, string, tuple,bool)
        - Actually need an object that is hashable, but think of as immutable as all immutable types are hashable
    - Be careful using `float` type as a key


## Lecture 15 Recursion
### RECURSIVE and BASE STEPS
-  **Recursive step**
    - Decide how to reduce problem to a **simpler/smaller version** of same problem, plus simple operations
-  **Base case**
    - Keep reducing problem until reach a simple case that can be **solved directly**

### WHAT IS RECURSION?
- Algorithmically: a way to design solutions to problems by divide-and-conquer or decrease-and-conquer
    - Reduce a problem to simpler versions of the same problem or to problem that can be solved directly
- Semantically: a programming technique where a function calls itself
    - In programming, goal is to NOT have infinite recursion
    - Must have 1 or more base cases that are easy to solve directly
    - Must solve the same problem on some other input with the goal of simplifying the larger input problem, ending at base case

### In recursion, each function call is completely separate.
- Separate scope/environments. Separate variable names. Fully I-N-D-E-P-E-N-D-E-N-T



## Lecture 16 Recursion on non-numerics
### Each case (base cases, recursive step) must return the same type of object
- Remember that function returns build upon each other!
- If the base case returns a bool and the recursive step returns an int, this gives a type mismatch error at runtime.

### INTUITION for WHEN to use RECURSION
- We did not know ahead of time how many times we needed to loop! (aka how many levels of if/else we needed)
- While loops kept iterating as long as some condition held true.

### PROBLEMS that are NATURALLY RECURSIVE
- A file system
- Order of operations in a calculator
- Scooby Doo gang searching a haunted castle
- Bureaucracy

### MAJOR RECURSION TAKEAWAYS
- Most problems are solved more intuitively with iteration
    - We show recursion on these to:
        - Show you a different way of thinking about the same problem (algorithm)
        - Show you how to write a recursive function (programming)
- Some problems have nicer solutions with recursion
    - If you recognize solving the same problem repeatedly, use recursion
- Tips
    - Every case in your recursive function must return the same type of thing
    - Your function doesn’t have to be efficient on the first pass
        - It’s ok to have more than 1 base case
        - It’s ok to break down the problem into many if/elifs
        - As long as you are making progress towards a base case recursively


## Lecture 17 Python classed
### Objects
- Each is an object, and every object has:
    - An internal data representation (primitive or composite)
    - A set of procedures for interaction with the object
-  An object is an instance of a type

### OBJECT ORIENTED PROGRAMMING (OOP)
- **EVERYTHING IN PYTHON IS AN OBJECT** (and has a type)
- Can create new objects of some type
- Can manipulate objects
- Can destroy objects
    - Explicitly using `del` or just “forget” about them
    - ython system will reclaim destroyed or inaccessible objects – called “garbage collection”

### WHAT ARE OBJECTS?
- Objects are a data abstraction that captures…
- (1) An internal representation
    - Through data attributes
- (2) An interface for interacting with object
    - Through methods
    (aka procedures/functions)
    - Defines behaviors but
    hides implementation

### ADVANTAGES OF OOP
- **Bundle data into packages** together with procedures that work on them through well-defined interfaces
- Divide-and-conquer development
    - Implement and test behavior of each class separately
    - Increased modularity reduces complexity
- Classes make it easy to reuse code
- Many Python modules define new classes
- Each class has a separate environment (no collision on function names)
- Inheritance allows subclasses to redefine or extend a selected subset of a superclass’ behavior

### CREATING AND USING YOUR OWN TYPES WITH CLASSES
- Make a distinction between **creating a class** and **using an instance** of the class
- Creating the class involves
    - Defining the class name
    - Defining class attributes
    - for example, someone wrote code to implement a list class
- Using the class involves
    - Creating new instances of the class
    - Doing operations on the instances
    - for example, `L=[1,2]` and `len(L)`

### A PARALLEL with FUNCTIONS
- **Defining a class** is like defining a function
    - With functions, we tell Python this procedure exists
    - With classes, we tell Python about **a blueprint for this new data type**
        - Its data attributes
        - Its procedural attributes
- **Creating instances of objects** is like calling the function
    - With functions we make calls with different actual parameters
    - With classes, we create new object tinstances in memory of this type

### DEFINE YOUR OWN TYPES
- Use the `class` keyword to define a new type
####
    class Coordinate(object):
        #define attribute here

### WHAT ARE ATTRIBUTES?
- Data and procedures that **“belong”** to the class
- **Data attributes**
    - Think of data as other objects/variables that make up the class
    - for example, a coordinate is made up of two numbers
- **Methods** (procedural attributes)
    - Think of methods as functions that only work with this class
    - How to interact with the object
    - for example you can define a distance between two coordinate objects but there is no meaning to a distance between two list objects

### DEFINING HOW TO CREATE AN INSTANCE OF A CLASS
- First have to define how to create an instance of class
- Use a special method called `__init__` to initialize some data attributes or perform initialization operations
####
    class coordinate(object):
        def __init__(self,xval,yval):
            self.x=xval
            sele.y=yval

- `self` allows you to create **variables that belong to this object**
- Without `self`, you are just creating regular variables!

### When defining a class, we don’t have an actual tangible object here.
- It’s only a definition

### DEFINE A METHOD FOR THE Coordinate CLASS
####
    def distance(self,other):
        x_diff_sq = (self.x-other.x)**2
        y_diff_sq = (self.y-other.y)**2
        return (x_diff_sq + y_diff_sq)**0.5

### THE POWER OF OOP
- **Bundle together objects** that share
    - Common attributes and
    - Procedures that operate on those attributes
- Use **abstraction** to make a distinction between how to implement an object vs how to use the object
- Build **layers** of object abstractions that inherit behaviors from other classes of objects
- Create our **own classes of objects** on top of Python’s basic classes


## Lecture 18 More python class methods
### SPECIAL OPERATORS IMPLEMENTED WITH DUNDER METHODS
- +, -, ==, <, >, len(), print, and many others are shorthand notations
- Behind the scenes, these get replaced by a method!
- Can override these to work with your class
- Define them with double underscores before/after
`__add__(self, other) # self + other`
`__sub__(self, other) # self - other`
`__mul__(self, other) # self * other`

### PRINT REPRESENTATION OF AN OBJECT
    >>> c = Coordinate(3,4)
    >>> print(c)
    <__main__.Coordinate object at 0x7fa918510488>
- Uninformative print representation by default
-  Define a `__str__` method for a class
- Python calls the `__str__` method when used with print on your class object

### WRAPPING YOUR HEAD AROUND TYPES AND CLASSES
- Use `isinstance()` to check if an object is a Coordinate
####
    >>> print(isinstance(c, Coordinate))
    True


## Lecture 19 Inheritance
### Access data attributes (stuff defined by `self.xxx`) through methods – it’sbetter style

### HIERARCHIES
- **Parent class** (superclass)
- **Child class** (subclass)
    - Inherits all data and behaviors of parent class
    - Add more info
    - Add more behavior
    - Override behavior

### INHERITANCE: PARENT CLASS
    class Animal(object):
        def __init__(self, age):
            self.age = age
            self.name = None
        def get_age(self):
            return self.age
        def get_name(self):
            return self.name
        def set_age(self, newage):
            self.age = newage
        def set_name(self, newname=""):
            self.name = newname
        def __str__(self):
            return "animal:"+str(self.name)+":"+str(self.age)

### INHERITANCE: SUBCLASS
    class Cat(Animal):
        def speak(self):
            print("meow")
        def __str__(self):
            return "cat:"+str(self.name)+":"+str(self.age)
- Add new functionality with `speak()`
    - Instance of type Cat can be called with new methods
    - Instance of type Animal throws error if called with Cat’s new method
- `__init__` is not missing, uses the Animal version

### WHICH METHOD TO USE?
- Subclass can have **methods with same name** as superclass
- For an instance of a class, look for a method name in current **class definition**
- If not found, look for method name **up the hierarchy** (in parent, then grandparent, and so on)
- Use first method up the hierarchy that you found with that method name

### A subclass can use a parent’s attributes, override a parent’s attributes, or define new attributes.
- Attributes are either data or methods.

### Class variables are shared between all instances.
- If one instance changes it,it’s changed for every instance.


## Lecture 20 Fitness tracker object-oriented programing example




## Lecture 21 Timing programs and counting operations
### EFFICIENCY IS IMPORTANT
- Separate time and space efficiency of a program
- Tradeoff between them: can use up a bit more memory
to store values for quicker lookup later
- Challenges in understanding efficiency
    - A program can be implemented in many different ways
    - You can solve a problem using only a handful of different algorithms
- Want to separate choice of implementation from choice of more abstract algorithm

### ASIDE on MODULES
- A module is a set of python definitions in a file
- You first need to “import” the module into your environment
####
    import time
    import random
    import dateutil
    import math
- Call functions from inside the module using the module’s name and dot notation
`math.sin(math.pi/2)`

### TIMING A PROGRAM
- Use time module
`import time`
- Recall that importing means to bring in that class into your own file
#### 
    def c_to_f(c):
        return c*9.0/5 + 32
    
    tstart = time.time()  #start clock
    c_to_f(37)  # call function
    dt = time.time() - tstart #stop clock
    print(dt, "s,")

### TIMING PROGRAMS IS INCONSISTENT
- GOAL: to evaluate different algorithms
- Running time **should vary between algorithms**

### COUNTING OPERATIONS
- Assume these steps take constant time:
    - Mathematical operations
    - Comparisons
    - Assignments
    - Accessing objects in memory
- Count number of
operations executed as
function of size of input

## Lecture 22 Big oh and theta
### Timing 
- Timing is a critical tool to assess the performance of programs
    - At the end of the day, it is irreplaceable for real-world assessment
- But we will see a complementary tool (**asymptotic complexity**) that has other advantages
    - A priori evaluation (before writing or running code)
    - **Assesses algorithm** independent of machine and implementation (what is intrinsic efficiency of algorithm?)
    - Provides direct insight into the design of efficient algorithms

### PROBLEMS WITH TIMING AND COUNTING
- **Timing** the exact running time of the program
    - Depends on **machine**
    - Depends on **implementation**
    - **Small inputs** don’t show growth
- **Counting** the exact number of steps
    - Gets us a **formula**!
    - **Machine independent**, which is good
    - Depends on **implementation**
    - **Multiplicative/additive constants** are irrelevant for large inputs
- Want to:
    - evaluate **algorithm**
    - evaluate **scalability**
    - evaluate **in terms of input size**

### ASYMPTOTIC GROWTH
- Goal: describe how time grows as size of input grows
    - Formula relating input to number of operations
- Given an expression for the number of operations needed to
compute an algorithm, want to know **asymptotic behavior as size of problem gets large**
    - Want to put a **bound** on growth
    - Do not need to be precise: **“order of” not “exact”** growth
- Will focus on term that grows most rapidly
    - Ignore additive and multiplicative constants, since want to know how rapidly time required increases as we increase size of input
- This is called order of growth
    - Use mathematical notions of “big O” and “big Θ” (Big Oh and Big Theta)

### BIG O Definition
- Big OH is a way to upper bound the growth of any function
- 𝑓(𝑥) = 𝑂(𝒈(𝒙)) means there exist constants 𝒄𝟎, 𝒙𝟎 for which 𝒄𝟎𝒈(𝒙) ≥ 𝒇(𝒙) for all 𝑥 > 𝒙𝟎

### BIG Θ Definition
- A big Θ bound is a lower and upper bound on the growth of some function

### Θ vs O
-  In practice, Θ bounds are preferred, because they are “tight"

### COMBINING COMPLEXITY CLASSES LOOPS IN SERIES
- Analyze statements inside functions to get order of growth
- Apply some rules, focus on dominant term
- Law of Addition for Θ():
    - Used with sequential statements
    - Θ(𝑓(𝑛)) + Θ(𝑔(𝑛)) = Θ(𝑓(𝑛) + 𝑔(𝑛))
- For example: Θ(𝑛) + Θ(𝑛 ∗ 𝑛) = Θ(𝑛 + 𝑛^2) = Θ(𝑛^2) because of dominant 𝑛^2 term
- Law of Multiplication for Θ():
    - Used with nested statements/loops
    - Θ(𝑓(𝑛)) ∗ Θ(𝑔(𝑛)) = Θ(𝑓(𝑛) ∗ 𝑔(𝑛))


## Lecture 23 Complexity classed examples
### CONSTANT COMPLEXITY
- Complexity **independent of inputs**
- Very few interesting algorithms in this class, but can often have pieces that fit this class
- **Can have loops or recursive calls**, but number of iterations or calls independent of size of input
- Some built-in operations to a language are constant
    - Python indexing into a list `L[i]`
    - Python list append `L.append()`
    - Python dictionary lookup `d[key]`
### LINEAR COMPLEXITY
- Simple iterative loop algorithms
    - Loops must be a function of input
- Linear search a list to see if an element is present
- Recursive functions with one recursive call and constant **overhead** for call
- Some built-in operations are linear
    - `e in L`
    - Subset of list: e.g.` L[:len(L)//2]`
    - `L1 == L2`
    - `del(L[5])`

### POLYNOMIAL COMPLEXITY (OFTEN QUADRATIC)
- Most common polynomial algorithms are quadratic, i.e., complexity grows with square of size of input
- Commonly occurs when we have nested loops or recursive function calls

### EXPONENTIAL COMPLEXITY
- Recursive functions where have more than one recursive call for each size of problem
    - Fibonacci
- Many important problems are inherently exponential

### LOGARITHMIC COMPLEXITY
- Complexity grows as log of size of one of its inputs
- Example algorithm: binary search of a list

### SEARCHING ALGORITHMS
- Linear search
    - Brute force search
    - List does not have to be sorted
- Bisection search
    - List **MUST be sorted** to give correct answer

### AMORTIZED COST-- n is len(L)
- Sort a list once then do many searches
- AMORTIZE cost of the sort over many searches
- SORT + K * Θ(log n) < K * Θ(n) implies that for large K, SORT time becomes irrelevant


## Lecture 24 Sorting algorithms
### BOGO/RANDOM/MONKEY SORT
- aka bogosort, stupidsort, slowsort, randomsort, shotgunsort
- To sort a deck of cards
    - throw them in the air
    - pick them up
    - are they sorted?
    - repeat if not sorted
- Best case: **Θ(n) where n is len(L)** to check if sorted
- Worst case: Θ(?) it is **unbounded** if really unlucky

### BUBBLE SORT
- **Compare consecutive pairs** of elements
- **Swap elements** in pair such that smaller is first
- When reach end of list, **start over** again
- Stop when **no more swaps** have been made
#### 
    def bubble_sort(L):
        did_swap = True
        while did_swap:
            did_swap = False
            for j in range(1, len(L)):
                if L[j-1] > L[j]:
                    did_swap = True
                    L[j],L[j-1] = L[j-1],L[j]
- Θ(n2) where n is len(L) to do len(L)-1 comparisons and len(L)-1 passes

### SELECTION SORT
- First step
    - Extract **minimum element**
    - **Swap it** with element at **index 0**
- Second step
    - In remaining sublist, extract **minimum element**
    - **Swap it** with the element at **index 1**
- Keep the left portion of the list sorted
    - At ith step, **first i elements in list are sorted**
    - All other elements are bigger than first i elements
#### 
    def selection_sort(L):
        for i in range(len(L)):
            for j in range(i, len(L)):
                if L[j] < L[i]:
- Complexity of selection sort is 𝚯(n^2) where n is len(L)             

### MERGE SORT归并排序
- Use a **divide-and-conquer** approach:
    - If list is of length 0 or 1, already sorted
    - If list has more than one element, split into two lists, and sort each
    - Merge sorted sublists
        - Look at first element of each, move smaller to end of the result
        - When one list empty, just copy rest of other list
- **Split list in half** until have sublists of only 1 element
- Merge such that **sublists will be sorted after merge**
#### 
    def merge(left, right):
        result = []
        i,j = 0, 0
        while i < len(left) and j < len(right):
            if left[i] < right[j]:
                result.append(left[i])
                i += 1
            else:
                result.append(right[j])
                j += 1
        while (i < len(left)):
            result.append(left[i])
            i += 1
        while (j < len(right)):
            result.append(right[j])
            j += 1
        return result
    
    def merge_sort(L):
        if len(L) < 2:
            return L[:]
        else:
            middle = len(L)//2
            left = merge_sort(L[:middle])
            right = merge_sort(L[middle:])
            return merge(left, right)
- Each recursion level does Θ(n) work and there are Θ(log n) levels, where n is len(L)
-  Overall complexity is **𝚯(n log n)** where n is len(L)

### 𝚯(n log n) is the fastest a sort can be

## Lecture 25 Plotting


## Lecture 26 List access, hashing, simulations and wrap-up

    