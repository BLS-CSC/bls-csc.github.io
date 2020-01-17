---
layout: default
title: Classes
---

# {{page.title}}

So far, we've been making rather simple programs. We've manipulated a few numbers, but not much more complicated. If we wanted organized data, we had lists and strings. However, they're not the only way to organize data.

Classes are the main method in which programmers group data, at least in modern [object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming). They consist of *states*, represented with instance variables, and *behaviors*, represented with functions, which we call *methods*.

## What we did before


Suppose we were learning to program a fighting game with two players. We might write a Processing program that looks like this:

```
health1 = 100
health2 = 100
item1 = None
item2 = None
x1 = 100
x2 = 500
y1 = 300
y2 = 300

def setup():
    size(600, 600)

def draw():
    clear()
    ellipse(x1, y1, 50, 50)
    ellipse(x2, y2, 50, 50)

def keyPressed():
    global x1, x2, y1, y2
    
    if key == 'w':
        y1 -= 5
    if key == 's':
        y1 += 5
    if key == 'a':
        x1 -= 5
    if key == 'd':
        x1 += 5
    
    if keyCode == UP:
        y2 -= 5
    if keyCode == DOWN:
        y2 += 5
    if keyCode == LEFT:
        x2 -= 5
    if keyCode == RIGHT:
        x2 += 5
```

There's a lot of redundant code here, from the two definitions of each variable, the two calls to ellipse, and the mess with keyPressed.

One solution would be to organize these both into lists and for-loop through instead, but there's a better way.

## Defining a class

With classes, we can organize data.

```
class Player:

    # Constructor
    def __init__(self):
        self.health = 100
        self.item = None
        self.x = 0
        self.y = 0
```

Let's break down the lines.
1.  `class Player:`
    
    Classes are denoted by the `class` keyword, the name of the class (`Player`), and a colon. This forms a new block in which all instance methods must be defined.
1.  `def __init__(self):`
    
    This line defines the constructor of the class. Constructors are called whenever an instance of a class is created, or, in this case, when we create a player. Constructors must be named `__init__`. We will address `self` soon.

1.  ```
    self.health = 100
    self.item = None
    self.x = 0
    self.y = 0
    ```

    These lines define instance variables of a class. *Instance variables* are variables which have unique states across objects. For example, the value of `health` can be 100 in one player object and 36 in another.
    Each of variables has class scope, meaning that they will be defined in all of the class' methods.

## Using classes

### Creating an instance

To create an *instance* of a class, you call the constructor like a function.

```
carrie = Player()
```
This creates a player object, which has instance variables `health`, `item`, `x`, and `y`.

```
mary = Player()
```
This line would create another instance of the player class, which has its own `health`, `item`, `x`, and `y`.

A good way to understand instances is with templates. A class is a template for an object with certain characterstics, and objects are the shapes created. The template is always the same, but the circles you draw and cut out of a page are distinct. You can move them independently, fold them differently, and, in general, change their states independetly.

If we replace all of those messy variables definition with objects, we can shorten our code a litte.

Let's start from the ground up.

```
# First define the Player class

class Player:

    # Constructor
    def __init__(self):
        self.health = 100
        self.item = None
        self.x = 0
        self.y = 0

# Create two instances of the player class

carrie = Player()
mary = Player()

def setup():
    size(600, 600)

```

### Accessing fields

All fields inside a class can be accessed with `dot notation`.

For example, if you wanted to access the `x` and `y` variables of `carrie`, you would write `carrie.x` and `carrie.y`.

Let's go ahead and rewrite the `keyPressed` function.

```
def keyPressed():
    global carrie, mary
    
    if key == 'w':
        carrie.y -= 5
    if key == 's':
        carrie.y += 5
    if key == 'a':
        carrie.x -= 5
    if key == 'd':
        carrie.x += 5
    
    if keyCode == UP:
        mary.y -= 5
    if keyCode == DOWN:
        mary.y += 5
    if keyCode == LEFT:
        mary.x -= 5
    if keyCode == RIGHT:
        mary.x += 5
```

We can also replace our `x`s and `y`s in `draw`.

```
def draw():
    clear()
    ellipse(carrie.x, carrie.y, 50, 50)
    ellipse(mary.x, mary.y, 50, 50)
```

#### A note about `self`

When we defined the class, we wrote a lot of `self`s. `self`, which must be defined as the first argument of an instance method, refers to the object which called the method. In the constructor, it refers to the object being created. Without `self`, Python would have to guess between creating a local variable, a global varible, and an instance variable. By requiring developers to refer to an object's fields through `self`, Python prevents this conflict.

## Writing Methods

There's something wrong with our Processing code above. It's longer and more inconvenient. What gives?

Well, remember when I defined a class, I said that they had both states and behaviors? We already made states. We're going to define a behavior now.

### Creating the `draw_me` mathod

Inside our class definition, define another method, called `draw_me`.

```
class Player:

    # Constructor
    def __init__(self):
        self.health = 100
        self.item = None
        self.x = 0
        self.y = 0

    def draw_me(self):
        ellipse(self.x, self.y, 50, 50)
```

Now each object has a behavior to draw itself!
Note how you can use `self` rather than refer to each object individually.

Now, in the `draw` function, replace the direct calls to ellipse with a call to the `draw_me` method.

```
def draw():
    clear()
    carrie.draw_me()
    mary.draw_me()
```

Now our code is organized.

## Advantages

### Abstraction

What we've just done is we've abstracted the drawing behavior. Before, to draw a player character, we had to know that we had to draw a circle centered at the player's x and y locations, with a radius 50. Now, anyone who wants to use the `Player` class only has to call `draw_me` to get the same, consistent behavior.

If you imagine that the `draw_me` method was even longer and more complicated, that we would save a lot time defining it once and using it multiple times.

### Organization

Also remember that instance methods are specific to classes. It would have been possible to write a function like this outside of the class:

```
def draw_plr(plr):
        ellipse(plr.x, plr.y, 50, 50)
```

In fact, this is standard behavior in C, where classes don't exist, and you can see how it carries over in the use of `self`. However, now imagine that you have another `draw` function for weapons, and another for map tiles. These can get out of hand, and you will write better code if you sort them neatly into their respective classes.

If you want to look at another advantage, check out [Duck typing](//en.wikipedia.org/wiki/Duck_typing) on Wikipedia.