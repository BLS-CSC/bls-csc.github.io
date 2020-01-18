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
    
    if key == 'i':
        y2 -= 5
    if key == 'j':
        y2 += 5
    if key == 'k':
        x2 -= 5
    if key == 'l':
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

A good way to understand instances is with templates. A class is a template for an object with certain characteristics, and objects are the shapes created. The template is always the same, but the circles you draw and cut out of a page are distinct. You can move them independently, fold them differently, and, in general, change their states independently.

If we replace all of those messy variables definition with objects, we can shorten our code a little.

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
    if key == 'w':
        carrie.y -= 5
    if key == 's':
        carrie.y += 5
    if key == 'a':
        carrie.x -= 5
    if key == 'd':
        carrie.x += 5
    
    if key == 'i':
        mary.y -= 5
    if key == 'k':
        mary.y += 5
    if key == 'j':
        mary.x -= 5
    if key == 'l:
        mary.x += 5
```

We can also replace our `x`s and `y`s in `draw`.

```
def draw():
    clear()
    ellipse(carrie.x, carrie.y, 50, 50)
    ellipse(mary.x, mary.y, 50, 50)
```

### A note about `self`

When we defined the class, we wrote a lot of `self`s. `self`, which must be defined as the first argument of an instance method, refers to the object which called the method. In the constructor, it refers to the object being created. Without `self`, Python would have to guess between creating a local variable, a global variable, and an instance variable. By requiring developers to refer to an object's fields through `self`, Python prevents this conflict.

## Writing Methods

There's something wrong with our Processing code above. It's longer and more inconvenient. What gives?

Well, remember when I defined a class, I said that they had both states and behaviors? We already made states. We're going to define a behavior now.

### Creating the `draw_me` method

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

## Writing the move method

If you take a look at our code, it might look something like this.

```
# Define the class

class Player:

    # Constructor
    def __init__(self):
        self.health = 100
        self.item = None
        self.x = 0
        self.y = 0

    def draw_me(self):
        ellipse(self.x, self.y, 50, 50)

# Create instances of the class (objects)

carrie = Player()
mary = Player()

# Processing

def setup():
    size(600, 600)

def draw():
    clear()
    carrie.draw_me()
    mary.draw_me()

# Handle key presses

def keyPressed():
    if key == 'w':
        carrie.y -= 5
    if key == 's':
        carrie.y += 5
    if key == 'a':
        carrie.x -= 5
    if key == 'd':
        carrie.x += 5
    
    if key == 'i':
        mary.y -= 5
    if key == 'k':
        mary.y += 5
    if key == 'j':
        mary.x -= 5
    if key == 'l:
        mary.x += 5
```

Notice where all the redundant code is: `keyPressed()`. Let's write a generalized `move` method to fix that.

As always, we start with a function definition.

```
def move(self):
    if key == 'w':
        carrie.y -= 5
    if key == 's':
        carrie.y += 5
    if key == 'a':
        carrie.x -= 5
    if key == 'd':
        carrie.x += 5
```

Now, let's generalize this method. First, we'll change occurences of `carrie` to `self`.

```
def move(self):
    if key == 'w':
        self.y -= 5
    if key == 's':
        self.y += 5
    if key == 'a':
        self.x -= 5
    if key == 'd':
        self.x += 5
```

Now, whatever object calls the move method (either `carrie` or `mary`) will be affected, rather than just `carrie`.

There's one more difference between `carrie`'s and `mary`'s behaviors: the keys pressed. `carrie` uses the WASD keys, whereas `mary` uses the TFGH keys. How do we account for this differences in one method?

### Adding method arguments

Like any other function, methods can take in arguments as input to modify their behavior.

Let's start by generalizing our `if` statements. Instead of writing the strings for individual keys, we can use variables to represent the target key.

```
def move(self):
    if key == up_key:
        self.y -= 5
    if key == down_key:
        self.y += 5
    if key == left_key:
        self.x -= 5
    if key == right_key:
        self.x += 5
```

Now, we need to define `up_key`, `down_key`, `left_key`, and `right_key` as method parameters.

```
def move(self, up_key, down_key, left_key, right_key): # Define parameters
    if key == up_key:
        self.y -= 5
    if key == down_key:
        self.y += 5
    if key == left_key:
        self.x -= 5
    if key == right_key:
        self.x += 5
```

Finally, we can replace our previous code with a call to the `move` method. Since the `move` method specifies four parameters for directional keys, we have to pass in four parameters representing directional keys.

```
# Handle key presses

def keyPressed():
    carrie.move('w', 's', 'a', 'd')
    mary.move('i', 'k', 'j', 'l')
```

Not only is our code a lot shorter, it's also a lot more readable and intuitive. When a key is pressed, we tell `carrie` and `mary` to move. Our code practically annotates itself without losing any functionality.

If we want to add any changes to the behaviors of the key presses, like adjust the speed from 5 to 10, we just have to modify the `move` method in a few places, rather than track down every `if` statement scattered in `keyPressed`.

## Modifying the constructor

TBD

## Challenges

Using the same principle of writing code once and using it multiple times, how could you modify the `move` method so that, to change the speed of the player, you only have to modify a single line of code?

Try to draw carrie and mary with different colors by modifying...
 * The `draw_me()` method
 * The constructor
Which method is better (aka more intuitive)?

Write a method that teleports one of the players when the mouse is clicked.

Write a method which can shoot projectiles.