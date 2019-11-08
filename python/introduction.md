---
title: Introduction
---

# {{page.title}}

Welcome to the BLS Comp Sci Club's Python tutorial!

Python is one of the most popular languages today. It's used for web servers, machine learning, science, and [calculators](//numworks.com)! Where do we even start learning?

## Getting Python

We use [repl.it](repl.it), but you will typically want a Python distribution on your own computer, which you can download from [the Python homepage](https://www.python.org/).

Make sure you get version 3!

## Using Python

First, you will want to open Python's REPL shell. On repl.it, it can be found on the right side of the screen. In a Python distribution, simply type `python3` into a command line or open up IDLE.

You will see something like this:
```
>>>
```
On repl.it, there is only one `>`, but it is functionally identical.

The first thing you will want to type in is probably basic mathematics. Type in `5 + 3` and press Enter.

Your output should resemble this:

```
>>> 5 + 3
8
>>>
```

Let's break down this piece of code.

`5` and `3` are both *integer literals*. They represent a value at its simplest form: itself. No evaluation needed.
`+` is an *operator*. Operators can be *unary* (taking one argument, like `-` in `-5`) or *binary* (taking one argument, like `-` in `5 - 3`).

Together, `5 + 3` is an *expression*. Like an expression in math, this is not a full *statement*, which can be properly run. Instead, it represents some value, after some evaluation. Note that `5` and `3` are also expressions.

Remember that an expression does not necessarily *do* anything. If you told someone "5 + 3", they might not do anything. Instead, if you said "evaluate 5 + 3", the request is clear.

Try something more complicated!

```
>>> 6 / ((5*2 + 3*7) / 3 + 8)
0.3272727272727272
>>>
```

Python returns this answer as a decimal, also called a *floating-point number*. As opposed to an integer, floating-point-numbers can be non-integer values, and they will have limited precision, since it only has 32 bits to work with.

As you can also see, when you type code, the spaces between operations is optional. You can even add more spaces, if need be.

There are a ton of other operations to work with!

 - `**` Exponentiation, akin to `^` in other contexts.
 - `&` Bitwise AND
 - `|` Bitwise OR
 - `^` Bitwise EXCLUSIVE OR
 - `~` Bitwise complement (invert bits)

I will admit that Python is extremely useful as a calculator. I will often use Python instead of my actual calculator for convenience on my homework.

## Check-in

1. What is a literal? Give an example.
1. What constitutes an expression?
1. What are the two types of operators?
1. What is a floating-point number?
1. What are two ways in which floating-points differ from integers?
1. Extra credit: what's your favoriate operator?

Once you know about operations and expressions, you are ready to learn about *statements*!

