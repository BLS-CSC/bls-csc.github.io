---
title: Variables and Built-in Functions
layout: default
---

# {{page.title}}

## Variables

In mathematics, we use variables to hold values which we would want to use multiple times. In Python, variables work the same way, holding any kind of Python object for later reference.

In Python, variables are defined using the simple notation `name = expression`.

For example, let's look at the following statement.
```
>>> my_favorite_number = 5 + 8
>>>
```

`my_favorite_number` is a *reference* to a variable. Our code *initializes* it to a value of 13. Before this point, `my_favorite_number` does not exist, and Python will raise an error if you try to evaluate it.

`=` is a *binary operator*, *assigning* the value on the right to the *reference* on the left

`5 + 8` is an expression, which is evaluated before the entire statement is.

Notice that there was no output. Since this is a statement, it may be impossible to evaluate this to a value.
For example, `5 + (num = 3)` is nonsense.
However, we can now use the variable as a number.

```
>>> my_favorite_number
13
>>>
```

This code evaluates `my_favorite_number`, which has a value of 13. The REPL then displays its value.

Check in: what is the value of `my_favorite_number * 2` at this point?

### Strings

Python has more than one type of variable. In fact, you can define an unlimited amount of variable types. But the one we want today is the string.

A string, defined by the class `str` in Python, is a string of characters. Effectively, it's a word, sentence, complete gibberish, or anything else which requires a bunch of characters to be put next to each other.

A string literal is defined using quotation marks. Valid string literals include `'cat'`, `"cat"`, and `"""cat"""`. (When you use three double quotes, the string is allowed to contain line breaks.)

These can also be placed inside variables.
```
my_name = 'Edward Yan'
```

## Putting stuff in files

All this may be useful, but when you open a program like [Blender](//blender.org), you aren't running a bunch of statements in a REPL. Instead, that code is placed into a set of files, which are compiled and run later.

In Python, we can do the same. In a file called `hello.py`, write some code, like the following lines:
```
my_num = 10
your_num = my_num / 2
```

Then, in a terminal window, type
```
$ python hello.py
```
You may need to type `python3` instead of `python`.

Here's what happens:
```
$ python hello.py
$
```

Nothing! (I hope.)

Our code does a few calculations and makes a few variables, but then we just let the code finish running without actually doing anything else. How do we put values in the console?

## Built-in Functions

Luckily, there are two built-in functions which help us! But before we explore built-in functions, we have to explore functions first.

### Functions

Functions, like in math, take in some inputs, do some calculations, and return an output. Except in Python, you can also return *no* output.

To call a function named `cat`, we write `cat()`.

An input, known as an *argument* in computer science, can be put inside the parentheses. Function arguments can be any valid expression. Multiple inputs are separated by commas.

For example, here are some valid function calls for a function named `cat` which takes in two numerical arguments:
```
cat(5, 10)
cat(my_num, 20)
cat(1 + 2, 3 / (my_num + 4*12))
```

### print()

`print` is one of the most helpful built-in functions in Python. It takes any number of arguments and puts them in the console, separated by a space. It then adds a newline character.

Try evaluating these print statements in the REPL shell.
1. `>>> print('Hi!')`
1. ```
>>> my_name = 'Dr. Nguyen'
>>> print(my_name)
```
1. ```
>>> my_real_name = [your actual name. Actually replace this text. Do not include the brackets.]
>>> print('Hello,', my_real_name)
```
Extra: try running `print(5)`. What does the error say? What can you guess about function arguments and types?
Also try running `print()`. What does that do?

### input()

`input()` is a function which receives input from the console in the form of a string. There is one optional argument, `prompt`, which is printed prior to receiving input.

Write these lines of code inside `hello.py`:
```
name = input('Your name:')
print(name)
```

When you run `python hello.py` in a terminal, you should see
```
$ python hello.py
Your name:_
```
Type in your name and press ENTER. You should see the the same thing printed back into the console.

```
$ python hello.py
Your name:BLS Comp Sci Club!!!
BLS Comp Sci Club!!!
$
```

## To Do

1. Change line 1 to `your_name = input('Your name:')`. What else in line 2 do you have to change?
1. Modify the code so that there is a space after `Your name:`.
1. Modify the code so that it properly prints Hello before the name.
1. Ask for their age after asking for their name and print it out. An example output might be `Hello, Sarah 19`
1. Extra: also tell people `Nice to meet you!`

Now that you can sort your code into files, it's time to explore some bulker code.
