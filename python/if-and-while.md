---
title: If Statements and While Loops
---

# {{site.title}}

Computers are great at doing mathematics, but computer programs are more than just a bunch of equations.

Computer programs should be able to respond to a user's input dynamically, possibly by checking certain conditions and taking different paths depending on the result.

Conveniently, that's what the if statement and while loop do!

## Boolean Values

Both if statements and while loops use something called a boolean, so it is important for us to understand those first.

Boolean (named `bool`) is a type in Python just like `int`, `float`, or `string`. A boolean value is either `True` or `False`.

`True` and `False` are both boolean literals, meaning that they are direct values for the simplest booleans.

### Boolean Expressions

Some expressions will have a boolean type. Many of these expressions will use some kind of equality operator.

Equality operator (binary)
- `==` is equal to
  - compares two Python objects of any type and sees if they are considered equal
  - `'dog' == 'cat'` is equivalent to `False`
- `!=` is not equal to
  - returns the opposite of `==`
  - `'dog' != 'cat'` is equivalent to `True`
- `<` Less than
  - compares two Python objects of any type and sees if the first is considered less than the second
  - `3 < 5` is equivalent to `True`
- `>` Greater than
- `<=` Less than or equal to
  - Note that this is not always the same as `<` or `==`. Sometimes this has a custom purpose.
  - `3 <= 3` is equivalent to `True`
- `>=` Greater than or equal to
  - Same mechanics as `<=`

There are also operators which operate on booleans.
- `and`: `a and b` is `True` when both booleans `a` and `b` are `True`
- `or`: `a or b` is `True` when at least one boolean, `a` or `b`, is `True`
- `not`: `not a` inverts a boolean value

Check:
What is the value of `((2 <= 3) and 'a' != 'b') or (not (5 > 3))`?

## If Statements

If statements check a condition to decide if a piece of code should or shoult not run.

If statements have some rather simple syntax:
```
if condition:
    # do stuff
    pass
```
`condition` is a boolean expression.

`:` denotes that a block is created. *Blocks* are sections of code which are grouped and run together

Note the indentation after the `:`. This is also important to denote where a block starts and ends.

`# do stuff` is a comment, which does nothing.
`pass` also does nothing, but it is important to Python since it provides the indentation needed for a block. An if statement with no block following it will raise a syntax error.

Here's an example of an if statement, with statistics courtesy of Wolfram Language:

```
name = input('Your name:')

if name == 'Liam' or name == 'Emma':
    print('Your name is the most commonly given name for your sex!')
    print('Good luck being unique.')

print('Hello,' name)
```

You can test the program with a few inputs to see what happens. Here's what you should see:
1. Inputting 'Liam':
    - ```
Your name is the most commonly given name for your sex!
Good luck being unique.
Hello, Liam
```
1. Inputting 'Emma':
    - ```
Your name is the most commonly given name for your sex!
Good luck being unique.
Hello, Emma
```
1. Inputting anything else, like 'Kat'
    - ```
Hello, Kat
```

Let's step through our program.
1. `name = input('Your name:')`
    - Asks for a name and stores the user's input in a variable `name`
1. `if name == 'Liam' or name == 'Emma':`
    - Checks to see if `name == 'Liam' or name == 'Emma'` is `True`.
        - First, check if `name == 'Liam'` is `True`. If it is, then the whole expression is `True`. Skip checking the second boolean value.
            - The process of skipping checking a boolean if one condition is enough to know the value of the entire boolean is called *short-circuit evaluation*.
        - If not, check if `name == 'Emma'` is `True`. If it is, then the whole expression is `True`.
    - If the expression is `True`, enter the block and proceed to the next line.
    - If not, skip the whole block and go to the first unindented line.
1. ```
print('Your name is the most commonly given name for your sex!')
print('Good luck being unique.')
```
    - Prints out some text if run
1. `print('Hello,' name)`
    - Prints out 'Hello, \[name\]' regardless of whatever happened in the if block.

This is why indentation is so important in Python specifically. Indentation indicates exactly which block a line of code belongs to.

### Else and Else If

There are a few other statements related to the if statement.

The else statement is placed right after an if block ends and run when the if block fails to run.

The else if statement (written as `elif`) acts like an else block but contains a condition which is also tested before the else if block can be run.

Here's an example of both in use:
```
guess = int(input('Guess a number!'))

if guess == 43:
    print('Wow! You\'re pretty good at guessing.')
elif guess < 10:
    print('Your guess is way too low!')
elif guess < 43:
    print('You guessed too low.')
elif guess < 80:
    print('You guessed too high.')
else:
    print('You guessed way too high!')

print('Thanks for playing!')
```
Notice: `print('Wow! You\'re pretty good at guessing.')` is written correctly. The `\` indicates an *escape character*, which is a special character which would normally mean something in Python. Without the slash, the string would end after `You`, and the rest would be an error.

Run this code for yourself and test a few inputs!
There are a few things you should notice.
1. Since `input()` returns a string, we need to write `int(input())`, which converts the string to an integer value which we can properly compare.
1. Only one of the if, elif, end else blocks is run. After it is run, the rest of the blocks are skipped.
1. The if, elif, and else blocks run in order. A guess of 3 is less than 43, but since the condition `guess < 10` is reached first, `Your guess is way too low` is printed out, and not `You guessed too low.`
1. Because an else statement catches all other conditions, it must be placed at the end of the list.
1. `Thanks for playing!` is always printed out, since it is outside the previous if, elif, and else blocks.

This guessing game works, but it's pretty inconvenient to run a program multiple times to guess multiple times.
It would also be difficult to randomize the goal number, since every time you run a file, everything is reset.

## While Loops

While loops run *while* a certain condition is met. Unti that condition is met, Python runs the entire next block repeatedly. The condition is only checked before the block is run or rerun, not in the middle of the block, although there are [ways](https://www.tutorialspoint.com/python/python_loop_control.htm) to break the natural flow of a loop.

```
while condition:
    # do stuff
    pass
```

The syntax is almost the same as an if statement. The only difference is that elif and else do not exist for while loops.

This is an error:
```
while 1 != 2:
    print('Reality is working.')
else:
    print('Reality has broken.')
```
Run it yourself to see exactly what Python says!

However, if you think about it, that ususally isn't a problem.
Here's an example showing why:
```
while num != 3:
    # do stuff
    pass
print(num)
```
If the while loop stops naturally, then what number should be printed out?

Here's our guessing game implemented with a while loop

```
guess = None

while guess != 43:
    guess = int(input('Guess a number!'))

    if guess == 43:
        print('Wow! You\'re pretty good at guessing.')
    elif guess < 10:
        print('Your guess is way too low!')
    elif guess < 43:
        print('You guessed too low.')
    elif guess < 80:
        print('You guessed too high.')
    else:
        print('You guessed way too high!')

print('Thanks for playing!')
```

Explanation:
1. `guess = None` declares `guess` to tell Python that `guess != 43` is not an error.
1. `guess = int(input('Guess a number!'))` asks for input every time the loop runs or reruns when `guess != 43`.
1. When `guess != 43` is `False` before the block is run again, the loop ends, and `Thanks for playing!` is printed.

## Challenge Problem

I moved the line `print('Wow! You\'re pretty good at guessing.')` outisde of the loop, since, if we exited the loop, the player would have guessed correcty anyway.
Where's the mistake?

```
guess = None

while guess != 43:
    guess = int(input('Guess a number!'))

    if guess < 10:
        print('Your guess is way too low!')
    elif guess < 43:
        print('You guessed too low.')
    elif guess < 80:
        print('You guessed too high.')
    else:
        print('You guessed way too high!')

print('Wow! You\'re pretty good at guessing.')
print('Thanks for playing!')
```

Hint: It's not an explicit Python error, like a syntax error. Instead, the mistake is unintended behavior.

If you can't find the solution, step through the program in your head with different inputs. Be specific! Don't say "guess is a number less than 10"; say "guess is 3".