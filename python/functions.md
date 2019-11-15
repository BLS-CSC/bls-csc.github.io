---
layout: default
title: Functions
---

# {{page.title}}

At some point, we might need to do some more complex operations multiple times.

Imagine drawing all the parts of a dropdown box over and over again whenever you needed another dropdown menu. Sure, you could copy code, but then you would just have even more code to modify individually if anything changes.

This is where a *function* comes in. A function is just a piece of code which can be run multiple times. Functions can take in input and return an output, almost like an internal mini-program.

Defining a function is as follows:
```
def name(arguments):
    # Function body
    pass
```

- `def` is required for function definitions
- `name` is whatever name you give your function. Variable naming rules apply.
- `arguemnts` is an optional list of comma-separated variable names to take as input.
- The function is grouped into a block.

To call a function, you refer to its name and specify arguments.
```
name(arguments)
```

## An example

Here's an example function:
```
def greet(name):
    print('Hello,' name)
    print('It's nice to meet you.')
```
The function greet accepts one argument, `name`, and runs the next few lines like normal.

To call this function, you run
```
greet('Mia')
```
This will output
```
Hello, Mia
It's nice to meet you.
```

Imagine that something like this happens behind the scenes:
```
name = 'Mia'
print('Hello', name)
print('It's nice to meet you.')
```

We can call the function again with different names.
```
greet('Mia')
greet('Bea')
greet('Thea')
```
outputs
```
Hello, Mia
It's nice to meet you.
Hello, Bea
It's nice to meet you.
Hello, Thea
It's nice to meet you.
```

## Function Arguments

Functions can take in any number of arguments, depending on what the programmer wants.

```
def sum(n1, n2):
    # Do some adding
    pass
```

You must specify a valid number of arguments when you call a function. You must include all required arguments and not include any extras.
```
sum(0)              # Not valid
sum(0, 1)           # Valid
                    # n1 becomes 0, and n2 becomes 1
sum('fri', 'end')   # Technically valid, but may cause some errors
sum(0, 4, 6)        # Not valid
```

### Default Arguemnts

You can specify default values for some arguments as well. Default values can be given when the function is called, but are optional.
```
def sum(n1, n2=5):
    # Do some adding
    pass

sum(0)              # Valid
                    # n1 becomes 0, and n2 becomes 5
sum(0, 1)           # Valid
                    # n1 becomes 0, and n2 becomes 1
sum('fri', 'end')   # Technically valid, but may cause some errors
sum(0, 4, 6)        # Not valid
```

### Check-in

You can call a certain function in the following ways:
```
do_stuff(0)
do_stuff('that')
do_stuff(1, 5)
do_stuff(1, 5, 8)
do_stuff(1, 'not', 8)
```
Write a valid function definition for that function. You do not have to write the function's code, nor do you have to know what it does.

## Return values

A function can also return a value, meaning that the function exits and the original function call is given a value.
In technical terms, the function returns a value to a *function caller*.
This means that a function call can be an expression.

```
def sum(n1, n2):
    return n1 + n2

print(sum(0, 1))    # prints 1
n = sum(5, 7)
print(n)            # prints 12
print(sum(sum(3, 6), 1))    # prints 10
```

You can include multiple return statements, although this is only useful with conditionals.
```
def abs_subtract(n1, n2):
    if n1 > n2:
        return n1 - n2
    else:
        return n2 - n1
    print('Haha this code is totally useless!')

print(abs_subtract(2, 7))   # 5
print(abs_subtract(7, 2) - 2)   # 5 - 2
```
outputs
```
5
3
```
The function `abs_subtract` always returns a value before the print statement runs, always preventing the last line from running.

### A really important note about return and print!

Returning and printing are not the same thing. Please do not use them interchangeably.

Returning a value simply transfers a value from inside the function to the function call, like evaluating a long math expression in your head.

Printing involves putting text on a console, like writing down the answer to a math problem.

Calling a function which returns a value without printing its result will not produce an output.
A line that reads `sum(1, 6)` won't do anything significant! Nothing is printed, nad if its value isn't saved to a variable or used as an argument for another function, then it is lost.

### Check-in

Considering that a function's execution terminates when a value is returned, how can you write the `abs_subtract` function without using `else` or another `if` statement?

## A word about scope

All variables have *scope*, a range where the variable is defined and valid.

So far, we've worked with variables with *global scope*, meaning they are valid throughout the program after being defined.

However, variables defined inside a function, including arguments, have *function scope*, a type of *local scope*. Outisde of their scope, they are invisible or undefined. This prevents your code from having to avoid too many variable names.

```
n = 5

def do_stuff(n. k): # These variables n and k only exist inside a single function call for do_stuff
    print(n)    # Prints out n

def do_other_stuff(n):  # This n only exists in a function call for do_other_stuff
    n = 2   # Sets the local n to 2
    j = 5   # Creates a local variable

do_stuff(3, 8)
do_other_stuff(7)

print(n)    # prints 5, because those other n's are different!

print(k)    # Not valid!
print(j)    # Not valid!

```

My output:
```
3
5
Traceback (most recent call last):
  File "test.py", line 15, in <module>
    print(k)    # Not valid!
NameError: name 'k' is not defined
```
`k` is out of scope!

## Best practices

Use functions for any kind of "template" code.

In general, try to use arguments to specify independent variables. If you want to specify constants, use default arguments.

## Practice

1. Write a function to calculate one of the roots of a quadratic.
1. Write a function which takes in a number and plays the guessing game from before with that number as the goal (instead of 43).
1. Write a function which calculates the factorial of a number.
