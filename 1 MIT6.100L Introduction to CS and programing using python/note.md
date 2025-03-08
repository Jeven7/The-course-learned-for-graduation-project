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

