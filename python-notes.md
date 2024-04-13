# Learning Python

This notebook covers various aspects of learning the python programming language.

## Variables

A variable is a label which points to a value which is stored in memory. The values could be **mutable** or **immutable**.

We can picture this as a container (the space created in memory) being given a value (the value at the memory address) and then a label being placed onto the container (this is the variable name).

We use an **assignment operator** to assign a value to a variable.

We can assign more than one variable at once. This makes sense if the variables are related to each other in some meaningful way.

```python=
x = 5
y = x
z = x + y
print(x)
print(y)
print(z)
```

```
5
5
10
```

```python=
a, b, c = 1, 2, 3
print(a)
print(b)
print(c)
```

```
1
2
3
```

### Variable Reassignment

We can reassign new values to variables. We need to remember that in python everything is an object. Variables have **object identifiers** - we can use these to see and understand more about what is happening with variable reassignment.

When we are assigning **immutable** datatypes to variables, we cannot change the original value - it remains in memory until all references to it have been removed and the garbage collector has subsequently removed it.

```python=
x = 5
alias_x = x
print(id(x))
print(id(alias_x))
x = 10
print(x)
print(alias_x)
print(id(x))
print(id(alias_x))
```

```
139630845591920
139630845591920
10
5
139630845592080
139630845591920
```

### Varibale Naming Conventions

In python, we like to use **snake_case** for variable names. The name should be something which is related to the value which is assigned to it.

We cannot use python key words. We must use letters or underscores to start variable names. The rest of the variable name can include numbers as well as letters and underscores.

>[!IMPORTANT]
>Variable names in python are case sensitive.

**Constant variables** should be written in uppercase letters along with underscores if necessary.

Python classes should be named as **UpperCamelCase** aka **PascalCase**.

Double UNDERscore variables - **dunder** - variables which start and end with two underscores are private and are generally meant to be left as they are.

## Data Types

There are lots of **data types** in python, but some are used more than others.

- Strings are sequences of characters.
- Integers are whole numbers.
- Floats are decimal numbers but they lack precision.
- Decimals are decimal numbers with more precision - they need to be imported from the standard library.
- Booleans are True and False values - they use less memory than using values such as 0 or 1 which are integers.

There are more complex data types which contain other data types - these are known as **data structures** or **collections**.

- Lists are ordered collections of data types.
- Dictionaries are unordered key:value pairs.

There is also a `None` type which just specifies that nothing is there.

Python is **dynamically typed** - this means that variables can have different data types assigned to them.

We can **cast** data types to different data types using functions such as `str()` or `int()`

```python=
name = "Billy"
age = 12
is_adult = False
child = None

billy_l = [name, age, is_adult, child]
sarah_d = {
    name: "Sarah",
    age: 22,
    is_adult: True,
    child: "Mary"
}

print(type(name))
print(type(age))
print(type(is_adult))
print(type(child))
print(type(billy_l))
print(type(sarah_d))

name = 18
age = "Billy"
is_adult = None
child = False
billy_l = {
    name: "Billy",
    age: 12
}
sarah_d = [name, age]

print(type(name))
print(type(age))
print(type(is_adult))
print(type(child))
print(type(billy_l))
print(type(sarah_d))

a = 8
print(type(a))
b = str(a)
print(type(b))
c = int(b)
print(type(c))
```

```
<class 'str'>
<class 'int'>
<class 'bool'>
<class 'NoneType'>
<class 'list'>
<class 'dict'>
<class 'int'>
<class 'str'>
<class 'NoneType'>
<class 'bool'>
<class 'dict'>
<class 'list'>
<class 'int'>
<class 'str'>
<class 'int'>
```

### Strings

Strings are created using `""` or `''` - we need to be consistent in the open and close characters used.

Strings are sequences of characters which are enclosed in the `""` or `''`

Strings are **immutable** data types.

#### Escape Characters

We can escape strings using `\` before specific characters.

- \n creates a new line
- \t is a tab
- \" or \' for quotations
- \\ for a back-slash

```python=
print("\tHello, how are you?\n")
input()
print("He said, \"I like food.\"\n")
print("This \\ is a back-slash.")
```

```
	Hello, how are you?


He said, "I like food."

This \ is a back-slash.
```

#### String Methods

There are lots of methods which we can call on strings.

- .lower()
- .upper()
- .title()
- .split(' ')
- .rstrip('!')
- .replace('hello', 'goodbye')
- .format(name, age)

```python=
msg = "This is a message. Hello, Billy-Bob!"
print(msg)
print(msg.lower())
print(msg.upper())
print(msg.title())
print(msg.split(' '))
print(msg.rstrip('!'))
print(msg.replace('Hello', 'Goodbye'))

name = "Jimmy Boy"
age = 22
print("Hello, {} - you are {} years old.".format(name, age))
```

```
This is a message. Hello, Billy-Bob!
this is a message. hello, billy-bob!
THIS IS A MESSAGE. HELLO, BILLY-BOB!
This Is A Message. Hello, Billy-Bob!
['This', 'is', 'a', 'message.', 'Hello,', 'Billy-Bob!']
This is a message. Hello, Billy-Bob
This is a message. Goodbye, Billy-Bob!
Hello, Jimmy Boy - you are 22 years old.
```

#### Formatting Strings

The `.format()` method is one way to combine data types into a string.

The latest way is to use an **fstring** - we just put `f""` - we can then use `{}` so python will interpolate what is inside the curly brackets.

```python=
name = "Jane"
age = 18
print("Hello, {} - you are {} years old.".format(name, age))
print()
print(f"Hello, {name} - you are {age} years old.")
print(f"{name} - in ten years you will be {age + 10} years old.")
```

```
Hello, Jane - you are 18 years old.

Hello, Jane - you are 18 years old.
Jane - in ten years you will be 28 years old.
```

#### String Indexing and Slicing

We can retrieve specific parts of a string using **indexing** or **slicing**.

Strings are indexed from 0 - we can use these positive indexes. They are also negatively indexed from the last character which is at position -1 We can index this way, too.

```python=
msg = "abcdefgh"
print(msg[0])
print(msg[7])
print()
print(msg[-1])
print(msg[-8])
```

```
a
h

h
a
```

We can **slice** strings using `:`

The slice will include the first specified index but not the last. We can slice using negative indexes, too.

>[!IMPORTANT]
>Slices **do not** include the last specified value

```python=
msg = "abcdefgh"
print(msg[0:3])
print(msg[-3:-1])
print(msg[4:6])
print(msg[4:])
print(msg[:5])
print(msg[:])
```

```
abc
fg
ef
efgh
abcde
abcdefgh
```

### Numbers and Mathematical Operations

We can use mathematical operators with **integers**, **floats** and **decimals**.

- add +
- subtract -
- multiply *
- divide (always returns a float) /
- exponent **
- floor division (always returns an integer) //
- mod (returns the remainder) %

We can round decimal numbers to a specified number of decimal places using the `round()` function.

```python=
a = 8
b = 4
print(a + b)
print(a - b)
print(a * b)
print(a / b)
print(a ** b)
print(a // b)
print(a % b)

c = 100 / 3
rounded_c = round(c, 2)
print(rounded_c)
```

```
12
4
32
2.0
4096
2
0
33.33
```

## Truthiness and Falsiness

Python objects have an inherent **truthiness** or **falsiness** to them. Examples of falsy objects are None data type, empty strings and the value 0. Examples of truthy objects are values above 0, a list of values and a string.

## Comparison Operators

We can use the following signs to make comparisons.

- `==` equal to
- `!=` not equal to
- `>=` greater than or equal to
- `<=` less than or equal to

We use `is` to check if two objects have the same place in memory.

## Assignment Operators

We can use **shorthand assignment operators** which assign new values to variables. An example is `score += 1` to replace `score = score + 1`

- +=
- -=
- *=
- /=

## Logical Operators

We can use `and`, `or` and `not`.

For a condition which uses `and` to be true, **both parts** of the condition must be true.

For a condition which uses `or` to be true, only **one part** of the condition must be true.

Using `not` makes the statement true if the opposite is true - it negates.

```python=
a = [1, 2, 3]
b = [1, 2, 3]
c = None
print(a == b)
print(a != b)
print(a is b)
print(not c)
n = 5
print(n <= 8)
n *= 8
print(n <= 8)
print(True and True)
print(False or True)
print(True or False)
print(not True)
print(not False)
```

```
True
False
False
True
True
False
True
True
True
False
True
```
## Control Flow - If Statements

We can change the flow of an algorithm's execution using **control flow** statements.

`If` statements execute a block of code if they are true. They skip the block of code if the statement (condition) is false.

We can add more cases using `elif` and we can use `else` as a final part.

We can nest `if` statements.

```python=
age = 21
if age >= 18:
    print("You are an adult.")
elif age >= 13:
    print("You are a teenager.")
else:
    print("You are a child.")
```

```
You are an adult.
```

```python=
choice = "west"
if choice == "west":
    print("You see a red door, a yellow door and a blue door.")
    choice_2 = "blue"
    if choice_2 == "red":
        print("A monster eats you!")
    elif choice_2 == "yellow":
        print("You suddently explode!")
    elif choice_2 == "blue":
        print("You escape - well done!")
    else:
        print("There is no such door - you set on fire!")
else:
    print("You went the wrong way and get lost.")
```

```
You see a red door, a yellow door and a blue door.
You escape - well done!
```

```python=
first_name = "Billy"
second_name = "Bob"
if first_name == "Billy" and second_name == "Bob":
    print("Hello, Billy Bob!")

name_1 = "Mary"
name_2 = "Susan"
if name_1 == "Mary" or name_2 == "Mary":
    print("Hello, Mary!")

if name_2 != "Mary":
    print("Sorry, I don't know who you are.")
```

```
Hello, Billy Bob!
Hello, Mary!
Sorry, I don't know who you are.
```

## Lists

Lists are one type of collection or data structure in python. There are many types of collection in python.

Collections are just collections of data types - they are needed so we can structure data - they are like bags which can have items added to them or removed from them.

Lists are *mutuable* data types. We can add and remove values to them and they remain in the same space in memory. They store objects in an ordered list. We can store other data types such as strings, integers and floats in lists. We can store lists inside lists.

We can mix data types in lists, but this is not recommended. We should use the same data type in a list.

Lists are ordered so the elements which are added to them have their order preserved.

Lists are created using `[]`

We can index and slice lists like we can strings. Lists are similar to strings because lists are sequences just like strings are. Strings are sequences of characters while lists are sequences of objects. Both strings and lists are *iterables* which means python can iterate over them.

There are *list methods* which we can use on lists. We look at ways we can grow lists below.

>[!NOTE]
>Lists take up less memory than other collections such as dictionaries, but they use more computational power to search through

```python=
names = ["charlie", "susan", "bob", "alice"]
print(names)
print(names[3])
print(names[:2])
print(id(names))

# append()
names.append("freddy") # adds an element at the end of a list
print(names)
print(id(names))

names_copy = names.copy()
print(id(names_copy))

# insert()
names_copy.insert(0, "lisa") # inserts an element at a position
print(names_copy)
print(names)

colours = ["red", "orange"]
colours_two = ["yellow", "green", "blue", "indigo", "violet"]
print(colours)
print(colours_two)

# extend() - this mutates the original list so be careful with it
# the += operator when used with lists is a shortcut for extend()
colours.extend(colours_two)
print(colours)

# we can do the same as extend() using +=
days = ["Monday", "Tuesday", "Wednesday"]
days_two = ["Thursday", "Friday", "Saturday", "Sunday"]
print(days)
print(days_two)
days += days_two
print(days)

# we can do the same as extend() but in an immutable way with +
letters = ["a", "b"]
letters_two = ["c", "d", "e"]
new_letters = letters + letters_two
print(new_letters)
print(id(letters))
print(id(letters_two))
print(id(new_letters))
```

```
['charlie', 'susan', 'bob', 'alice']
alice
['charlie', 'susan']
140558714044992
['charlie', 'susan', 'bob', 'alice', 'freddy']
140558714044992
140558714045504
['lisa', 'charlie', 'susan', 'bob', 'alice', 'freddy']
['charlie', 'susan', 'bob', 'alice', 'freddy']
['red', 'orange']
['yellow', 'green', 'blue', 'indigo', 'violet']
['red', 'orange', 'yellow', 'green', 'blue', 'indigo', 'violet']
['Monday', 'Tuesday', 'Wednesday']
['Thursday', 'Friday', 'Saturday', 'Sunday']
['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday']
['a', 'b', 'c', 'd', 'e']
140558714049984
140558714052096
140558714052736
```

### Other List Methods

There are other list methods. We can use them to remove items from lists or perform other actions on them.

```python=
# checking for membership
a = "bob" in names
b = "rupert" in names
print(a)
print(b)

# searching lists
print(names.index("susan"))
print(min(names))
print(max(names))

# sorting lists - mutable solution
names.sort() # sorts the list in place - mutable
print(names)

# sorting lists - immutable solution
unsorted_fruit = ["pineapple", "cherry", "banana", "apple"]
sorted_fruit = sorted(unsorted_fruit) # immutable solution
print(unsorted_fruit)
print(sorted_fruit)

# removing items
fish = ["tetra", "cod", "catfish", "danio", "gastro", "cod"]
print(fish)
fish.remove("cod") # we need to know the value
print(fish) # remove() only removes the first value if > 1 present

# using pop with an index
rt_fish = fish.pop(2) # pop() returns the popped value
print(fish)
print(rt_fish)
fish.pop() # pop() removes the last element by default
print(fish)
```

```
True
False
1
alice
susan
['alice', 'bob', 'charlie', 'freddy', 'susan']
['pineapple', 'cherry', 'banana', 'apple']
['apple', 'banana', 'cherry', 'pineapple']
['tetra', 'cod', 'catfish', 'danio', 'gastro', 'cod']
['tetra', 'catfish', 'danio', 'gastro', 'cod']
['tetra', 'catfish', 'gastro', 'cod']
danio
['tetra', 'catfish', 'gastro']
```

### Nested Lists

We can store lists inside lists - these are nested lists aka multi-dimensional lists. We do this when we want to store data as a table or a matrix.

We can index the list we want to use and then the item inside it.

```python=
nl1 = [["a", "b"], ["c", "d"], ["e", "f", "g", "h"]]
print(nl1[1][0])
```

```
c
```

We can iterate through items in nested lists by using nested for loops.

```python=
nl1 = [["a", "b"], ["c", "d"], ["e", "f", "g", "h"]]
for i in nl1:
    for val in i:
        print(f"List: {i} Value: {val}")
```

```
List: ['a', 'b'] Value: a
List: ['a', 'b'] Value: b
List: ['c', 'd'] Value: c
List: ['c', 'd'] Value: d
List: ['e', 'f', 'g', 'h'] Value: e
List: ['e', 'f', 'g', 'h'] Value: f
List: ['e', 'f', 'g', 'h'] Value: g
List: ['e', 'f', 'g', 'h'] Value: h
```

We can also use *list comprehension* with nested lists.

```python=
nl2 = [[val.upper() for val in i] for i in nl1]
print(nl1)
print(nl2)
nl3 = [[val for val in i] for i in nl1 if 'c' in i]
print(nl3)
nl4 = [[val.upper() for val in i] for i in nl1 if 'e' in i]
print(nl4)
```

```
[['a', 'b'], ['c', 'd'], ['e', 'f', 'g', 'h']]
[['A', 'B'], ['C', 'D'], ['E', 'F', 'G', 'H']]
[['c', 'd']]
[['E', 'F', 'G', 'H']]
```

## Functions

Functions are processes for executing tasks - they are used to save rewriting code. They can accept input and return output so they can give different results depending on the data passed to them.

Functions let us keep our code D.R.Y. - do not repeat yourself. This is the opposite of W.E.T. - write everything twice. This is because we can call the function time and time again.

Functions also let us abstract code away from development - we write the code in a function and then we don't have to see it or worry about it.

Functions let us logically order our code so it makes sense - this gets us away from spaghetti code because the functions do discrete tasks so we can organise our code better.

### Syntax

We use the `def` keyword along with `():` A block of code follows the `:` and parameters can be specified inside the `()`

We can then call the defined functions by specifying their name along with `()` and arguments included if they are needed.

```python=
def greeting():
    print("hello!")

greeting()
```

```
hello!
```

## Object Oriented Programming

OOP is a way of doing programming - it is a paradigm related to how we go about writing code and developing projects.

OOP lets us *encapsulate* data and behaviour in one object. This way of programming developed to let us model the real world in our code. Alan Kay was involved in this - he saw how organisms could communicate with one another without knowing much about the internal workings of each other. We do this all of the time. I communicate with my television without knowing how it works inside. I need a clearly defined interface (a remote control in this example) in order to do this. The interface is very important. Once an object has been created, its internal workings can be hidden from the programmer - they just need to know how to interact with it (use it in their programs).

OOP uses code to represent things from the real world such as a car, a deck of cards, a song, a schedule etc.

We use classes and objects in OOP.

We can see OOP as being like a factory - the *class* - from which we can create *instances* of it which are independent *objects* which are seperate from the class. Each instance of a class can be unique and different to the other instances.

### Classes

A class is essentialy a blueprint - a template - for how instances (objects) created from it are. The class contains *attributes* for its objects and *methods* which they can use.

>[!NOTE]
>A *method* is a *function* which is attached to an *object*

A class is like a cookie cutter - the objects created using it can be different even though they have the same attributes and methods.

### Instances (Objects)

Objects are constructed from a class blueprint - they contain the class properties and methods.

### Encapsulation

We aim to *encapsulate* (group) public and private attributes and methods into a class. Private just means it is only supposed to be used and referenced inside the class itself whereas public means it can be referenced and used elsewhere. This lets us represent different things which we need in our program. If we are making a poker game, for example, we could encapsulate attributes and methods to do with a user into one class, a deck of cards into another class, a card into another class and so on. We will then be able to better understand our code and work with it to create the game of poker.

### Abstraction

This means we hide the internal workings of objects and provide an interface to work with them.

```python
# a simple example of how objects are individual and unique
class Cookie(object): # no need to use object here in Python3
    pass

c1 = Cookie()
c2 = Cookie()
c3 = Cookie()

print(id(c1))
print(id(c2))
print(id(c3))
```

```
140581476118784
140581476114992
140581476121232
```

### Attributes

Attributes are the properties of objects - they are the data part of our classes.

We could see attributes as variables which belong to the local namespace of objects.

```python
# setting object attributes for c1
c1.buttons = "blue"
c1.scarf = "green"
# getting c1 attributes
print(c1.buttons)
print(c1.scarf)
# setting attributes for c2
c2.buttons = "red"
c2.scarf = "orange"
# getting c2 attributes
print(c2.buttons)
print(c2.scarf)
# setting attributes for c3
c3.buttons = "yellow"
c3.scarf = "purple"
# getting c3 attributes
print(c3.buttons)
print(c3.scarf)
```

```
blue
green
red
orange
yellow
purple
```

### Methods

Methods are functions which are attached to objects. They define the behaviours which objects can perform.

Methods are the interface - how we can interact with the object.

In order to define a method, we define a function inside a class. We use the *self* keyword to reference the object we are calling it on and we use dot notation to call it `mary.fullname()` for example.

```python
# working with methods - simple
class User(object):
    def full_name(self):
        return f"{self.first_name} {self.last_name}"
    def can_drive(self, min_age):
        return self.age >= min_age

mary = User()
mary.age = 20
mary.first_name = "Mary"
mary.last_name = "Brown"
print(mary.full_name())
print(mary.can_drive(18))
```

```
Mary Brown
True
```

```python
john = User()
john.age = 16
john.first_name = "John"
john.last_name = "Jones"
print(john.full_name())
print(john.can_drive(18))
```

```
John Jones
False
```

### Initializing

We can use the `__init__` method to set attributes on objects when they are instansiated from a class.

This is useful because we usually want instances of a class to have lots of attributes which are the same but with different values.

Using the __init__ method to initialise objects is a good way to make sure that they are instantiated correctly and consistently.

__init__ is a *dunder* method - these are also known as *magic methods* because we do not call it explicitly - python calls it itself.

>[!IMPORTANT]
>We should include an __init__ method in every class we create

```python
# using the __init__ method to initialise objects
class Fish(object):
    def __init__(self, order, colour, length):
        self.order = order
        self.colour = colour
        self.length = length
```

```python
billybob = Fish("catfish", "brown", 5)
print(billybob.order)
print(billybob.colour)
print(billybob.length)
```

```
catfish
brown
5
```

### Class Attributes

These are attributes which are linked with a class rather than individual objects which have been instantiated from the class. This means that all the objects created from the class can get the class attributes.

```python
class Bike(object):
    DEFAULT_COLOUR = "blue"
    def __init__(self, color):
        self.color = color

bike_1 = Bike("red")
print(bike_1.DEFAULT_COLOUR)
print(id(bike_1.DEFAULT_COLOUR))
bike_2 = Bike("red")
print(id(bike_2.DEFAULT_COLOUR))
print(bike_1.color)
print(id(bike_1.color))
print(bike_2.color)
print(id(bike_2.color))
bike_1.color = "yellow"
print(bike_1.color)
print(id(bike_1.color))
print(bike_2.color)
print(id(bike_2.color))
Bike.DEFAULT_COLOUR = "green"
print(bike_1.DEFAULT_COLOUR)
print(bike_2.DEFAULT_COLOUR)
print(id(bike_1.DEFAULT_COLOUR))
print(id(bike_2.DEFAULT_COLOUR))
```

```
blue
140572951488944
140572951488944
red
140572951488752
red
140572951488752
yellow
140572951488880
red
140572951488752
green
green
140572951488816
140572951488816
```

### Get and Set

In the example above, both `Bike` objects are getting the class attribute `DEFAULT_COLOUR` from the class. Python first of all looks into the object itself for the variable `DEFAULT_COLOUR` but does not find it so bubbles up to the *class memory space* and does find it.

If we try to set `DEFAULT_COLOUR` from an instance of `Bike` it will not work - Python will create a variable called `DEFAULT_COLOUR` in the *object memory space* and it will find this one first before the class attribute each subsequent time.

```python
bike_1.DEFAULT_COLOUR = "red"
print(bike_1.DEFAULT_COLOUR)
print(id(bike_1.DEFAULT_COLOUR))
print(Bike.DEFAULT_COLOUR)
print(id(Bike.DEFAULT_COLOUR))
print(bike_2.DEFAULT_COLOUR)
print(id(bike_2.DEFAULT_COLOUR))
```

```
red
140134846294256
blue
140134846294448
blue
140134846294448
```

### Accessing Class Attributes from Methods

We tend to access class attributes from methods. An example is to set default values if a value is not passed to the init method. We can reference the class attribute from inside methods using the self keyword or the name of the class.

```python
class Car(object):
    DEFAULT_COLOUR = "black"
    def __init__(self, make, colour=None):
        self.make = make
        if colour:
            self.colour = colour
        else:
            # self.colour = Car.DEFAULT_COLOUR
            self.colour = self.DEFAULT_COLOUR

car_1 = Car("bmw")
print(car_1.colour)
car_2 = Car("honda", "red")
print(car_2.colour)
```

```
black
red
```

### Keeping an Instance ID

One use case of a class attribute is having an id variable which keeps track of how many instances have been created. We could use something like this to keep track of how many players are in a game or to give each instance a unique id.

>[!NOTE]
>We need to use the *class name* when *setting* values to class attributes from within methods - self will not work

```python
class Player(object):
    ACTIVE_PLAYERS = 0
    DEFAULT_NAME = "anon"
    def __init__(self, name=None):
        if name:
            self.name = name
        else:
            self.name = self.DEFAULT_NAME
        Player.ACTIVE_PLAYERS += 1 # use the class name
    
    def logout(self):
        Player.ACTIVE_PLAYERS -= 1 # use the class name
        return(f"{self.name} logged out.")
    
p1 = Player("Barry")
p2 = Player()
print(Player.ACTIVE_PLAYERS)
print(p1.logout())
print(Player.ACTIVE_PLAYERS)
```

```
2
Barry logged out.
1
```

### Class Methods

Class methods are methods which are linked to a class rather than an instance of a class. We use them when the method does not need to know anything about the specifics of an instance whereas we use instance methods when the method does need to know something about the instance which is calling it.

>[!NOTE]
>Class methods often end up being used when a developer can not think of anywhere else to put the method - even though this is not ideal it happens

Class methods are defined following the `@classmethod` *decorator* and they use `cls` as the first passed argument rather than `self`.

```python
class Pets(object):
    PETS_CREATED = 0
    @classmethod
    def get_pet_number(cls):
        return cls.PETS_CREATED
    
    def __init__(self, species, name="Billybob"):
        self.name = name
        self.species = species
        Pets.PETS_CREATED += 1
    
cat_1 = Pets("cat")
print(Pets.get_pet_number())
fish_1 = Pets("catfish", "mobydick")
print(Pets.get_pet_number())
print(cat_1.name)
print(fish_1.name)
```

```
1
2
Billybob
mobydick
```

#### Class Method Example

Another example of when a class method could be used is when we want to turn data from one format to another before it is sent to the `__init__` method.

This example shows data which is in the form of a csv list coming into the method and then being unpacked into different data types before being sent to the `__init__` method to create an instance.

```python
class Book(object):
    @classmethod
    def from_str(cls, data_str):
        title, pages, price = data_str.split(",")
        # we pass the unpacked data to __init__
        return Book(title, pages, price)
    
    def __init__(self, title, pages, price):
        self.title = title
        self.pages = int(pages)
        self.price = float(price)

# we unpack csv data using a class method
book_1 = Book.from_str("Matilda,382,2.99")
print(book_1.title)
```

```
Matilda
```

### Magic Methods

Magic methods simply refers to methods which we do not invoke directly - python invokes them for us.

The most common magic method is `__init__` becuase we use it in every class we create. This method is magic because we do not directly invoke it - python invokes it when we instantiate a new object from a class.

>[!NOTE]
>Magic methods are also known as *dunder methods* because of the double underscore at the start and end of them

#### __str__

The `__str__` magic method returns a human readable string representation of an object. This is used so we know more easily what each object is. We could see this as a human way to refer to objects - in the example below we will be thinking about motorcycles - the human way to refer to one is something like *honda fireblade*

```python
class Motorcycle():
    def __init__(self, make, model, cc, year):
        self.make = make
        self.model = model
        self.cc = cc
        self.year = year
    
    def __str__(self):
        return f"{self.cc}cc {self.make} {self.model} ({self.year})"

bike_1 = Motorcycle("honda", "fireblade", 650, 2008)
print(bike_1) # without the __str__ magic method we could get a memory address returned
```

```
650cc honda fireblade (2008)
```

>[!NOTE]
>Without the `__str__` magic method we would get a memory address returned - for example: `<__main__.Motorcycle object at 0x7f6e04e27850>`

#### __repr__

The `__repr__` magic method is like the `__str__` magic method but it is more for machines rather than humans.

It will look more like code than regular human language.

```python
class Motorcycle():
    def __init__(self, make, model, cc, year):
        self.make = make
        self.model = model
        self.cc = cc
        self.year = year
    
    def __repr__(self):
        return f"Motorcycle(make={self.make}, model={self.model}, cc={self.cc}, year={self.year})"
bike_1 = Motorcycle("honda", "fireblade", 650, 2008)
bike_1 # if we use print() we will invoke __str__
```

```
Motorcycle(make=honda, model=fireblade, cc=650, year=2008)
```

>[!TIP]
>The returned value of `__repr__` should ideally be able to be used to instantiate a new object from a class

### Interfaces and Magic Methods

Interfaces are ways which we can interact with the attributes and methods of objects.

Python uses the same interfaces for lots of different things.

An example of this is the `+` operator which can be used to add integers, concatanate strings, join lists and more.

Another example is the `in` keyword for testing membership. This can be used to check if characters are in strings, objects are in lists, integers are in ranges and more.

One more example is how we can use `[]` to access elements in lists, items in dictionaries, characters in strings and more.

We can implement these interfaces - and many more - by using *magic methods* in our own classes.

>[!IMPORTANT]
>We want to make interaction with objects instantiated from our own classes as intuitive as possible - we therefore like to use interfaces which are consistent

An example of this is given below.

We can imagine that we are creating card games and in order to do so we have created a class for card objects.

The card objects have a value attribute which we intend to be used to add the values of cards together.

```python
class Card():
    def __init__(self, value, suit):
        self.value = value
        self.suit = suit

hearts_5 = Card(5, "hearts")
diamonds_8 = Card(8, "diamonds")

print(hearts_5.value)
print(diamonds_8.value)
```

```
5
8
```

For somebody who has not seen the code inside our class, the most intuitive way to add the values of `Card` objects together would be to use the commonly used `+` operator as the interface. This, however, does not work at the current time. If we try `hearts_5 + diamonds_8` we will receive a `TypeError`

One way to implement the functionality of being able to add `Card` objects would be to define an `add` method in the class.

```python
def add(self, other_card):
    return self.value + other_card.value
```

This works but in order to use it a developer would need to code: `total = hearts_5.add(diamonds_8)` which is not at all intuitive since it does not follow a consistent approach.

There is a better way.

We can use the `__add__` magic method which python gives us. This will allow developers to use the `+` operator as an interface to add together the values of `Card` objects. We simply need to make our current `add` method a *dunder* magic method: `__add__`

```python
def __add__(self, other_card):
    return self.value + other_card.value
```

The full code of the class and an example of how a developer can now use `+` to add the values of `Card` objects is given below.

```python
class Card():
    def __init__(self, value, suit):
        self.value = value
        self.suit = suit
    
    def __add__(self, other_card):
        return self.value + other_card.value

hearts_5 = Card(5, "hearts")
diamonds_8 = Card(8, "diamonds")

total = hearts_5 + diamonds_8

print(total)
```

By using magic methods in this way, we can make working with classes which we create a lot more intuitive. The reason for this is that as humans we will use what we already know when we approach new things. In this case, if a developer wants to add together two cards in a game they are creating which uses objects instantiated from our `Card` class, they will naturally try `+` first of all and they will expect it to work as intended - we can make this happen using the `__add__` magic method.

>[!IMPORTANT]
>Using *magic methods* makes our python code clean and easy to work with

### Equality and Magic Methods

Before we consider how we can use the `__eq__` magic method in python, it is worth taking the time to reflect on what it means to say that things are *equal*.

Let us take two shirts as an example. We might say that they are equal if they are the same colour and same size. This works for everyday use - for example when buying a shirt we will generally consider all of the small white shirts to be the same and therefore choose any of them off the rack.

But some people might be more picky and realise that some of the shirts have imperfections such as small holes in them or a thread of coton sticking out somewhere. In this view of being equal, we might consider 7 of the 10 shirts on the rack as being equal because we cannot see imperfections but the other three as not being equal because they have some kind of problem. We would then choose one of the seven shirts which we consider to be equal.

Somebody else might think about it more and realise that on an atomic level of course none of the shirts are equal - each one has a different atomic configuration.

We therefore define equality in a relative way which suits the needs of the context we are working in.

#### Equality in Python Using ==

By default, when python checks equality using `==` it performs a strict check which means it is checking if the two objects have the same space in memory. It will return `True` if they do and `False` if they do not.

```python
clubs_3 = Card(3, "clubs")
spades_3 = Card(3, "spades")

print(clubs_3 == spades_3)
print(id(clubs_3))
print(id(spades_3))
```

```
False
0x7f58c9477f70
0x7f58c9477f10
```

##### __eq__

We can define in our own classes what we want equality to mean. This can be achieved by using the `__eq__` magic method which will then let developers use `==` to check equality of objects instantiated from our class in a specified way.

>[!CAUTION]
>Before using `__eq__` we need to very carefully consider what equality means in our class and whether or not that will ever change

We could, for example, decide that for `Card` objects we want their equality to be based on their values. In this case, we could use the `__eq__` magic method as shown below.

```python
def __eq__(self, other_card):
    return self.value == other_card.value

clubs_3 = Card(3, "clubs")
spades_3 = Card(3, "spades")

print(clubs_3 == spades_3)
print(hearts_5 == spades_3)
```

```
True
False
```

We need to be careful before we use `__eq__` What if in this example we need equality to be based on the suit rather than the value? Problems such as this could lead to lots of work refactoring code.

>[!NOTE]
>We do not lose the ability to perform strict memory location equality checks if we implement our own version of `__add__` because the `is` keyword still does it

There are other comparison magic methods available such as `__lt__` for less than and `__gt__` for greater than.

### Inheritance

Classes can *inherit* attributes and methods from other classes - this is known as *inheritance*. Methods are inherited and anything else which has been defined at a *class level* such as *class attributes*. Attributes defined in an `__init__()` method are not inherited though there is a way to achieve this - covered below in the `super()` section.

This is useful because we might want to use the same attributes and / or methods which are already in a class. We can also modify these things once a class has inherited them.

An example might be we have a parent class which defines what a vehicle can do, and we then want to create a class to specify what a motorcycle can do and one which specifies what a car can do. Since both are vehicles they will need to inherit from the Vehicle class - we can then add methods and attributes which are specific to motorcycles and cars. In this way, we build on parent classes.

If we modify a parent method in a child class, python will look in the child class first and use that method rather than the one in the parent class. If the method does not exist in the child class, python will bubble up and look for it in the parent class.

In order to use inheritance, we pass the *parent* class to the *child* class as an argument to its definition.

A good way to understand *inheritance* is to think: *child is a / an parent* for example *`Fish` is an `Animal`*

```python
class Animal:
    plant = False
    def __init__(self):
        self.eyes = 2
        
    def breathe(self):
        return "I am breathing."
    
    def defending(self):
        return "I am defending my territory."
    
class Fish(Animal):
    def __init__(self, species):
        self.species = species
    
    def breathe(self):
        return "I am breathing underwater."
    
    def swim(self):
        return "I am swimming."

nemo = Fish("clownfish")
print(nemo.species) # this attribute is found in the Fish class
print(nemo.defending()) # this method is inherited from Animal()
print(nemo.breathe()) # this is modified in Fish()
print(nemo.swim()) # this is added in Fish()
print(nemo.plant) # class attributes are inherited
# attributes from Animal __init__ are not inherited
# so the below line of code will throw an error

# print(nemo.eyes)

# checking classes the nemo object belongs to
print(isinstance(nemo, Fish)) # True
print(isinstance(nemo, Animal)) # True
```

```
clownfish
I am defending my territory.
I am breathing underwater.
I am swimming.
False
True
True
```

### Polymorphism

This is simply the idea that one thing can take many forms. In Python, this relates to the concept of what `self` is.

The following code shows how we could define the `__str__` magic method in several related classes.

```python
class Vehicle(object):
    def __str__(self):
        return "Object: Vehicle"

class Car(Vehicle):
    def __str__(self):
        return "Object: Car"
    
class Airplane(Vehicle):
    def __str__(self):
        return "Object: Airplane"
```

There is a lot of repetition - there must be an easier way to do this.

We could just define one `__str__` method at the top level class and use polymorphism to dynamically alter the returned values.

>[!TIP]
>When we notice common patterns in methods we tend to define one method at the top level class

In the example below we define `__str__` at the top level class which is `Vehicle` and code it so that it dynamically retrieves the class name of `self` - the question arises - what is `self`?

```python
class Vehicle(object):
    def __str__(self):
        return "Object: {}".format(self.__class__.__name__)

class Car(Vehicle):
    pass
    
class Airplane(Vehicle):
    pass
```

The value of `self` will depend on the type of object which called the `__str__` method. For an `Airplane` object `self` will be `Airplane` whilst for a `Car` object `self` will be `Car`

The resulting output is shown below.

```python
a = Airplane()
c = Car()

print(a)
print(c)
```

```
Object: Airplane
Object: Car
```

The above example shows us *polymorphism* in action - Python is determining the value of `self` at runtime.

Another example is given below.

```python
class Vehicle(object):
    def move(self):
        my_sound = self.sound()
        print("I'm moving, and I sound: {}".format(my_sound))

class Car(Vehicle):
    def sound(self):
        return "Brooooom"
    
class Airplane(Vehicle):
    def sound(self):
        return "Nnneeaoowww"

a = Airplane()
a.move()
c = Car()
c.move()
```

```
I'm moving, and I sound: Nnneeaoowww
I'm moving, and I sound: Brooooom
```

### super()

We can use `super()` from a child class to have access to anything we specify from the parent aka super class.

Coming back to the example above, we can get the initialization attributes from the `Animal()` class into the `Fish()` class by using `super().__init__()` in the `Fish()` class `_init__(self)` method. The example below shows this for a different `Animal()` subclass.

```python
class Bird(Animal):
    def __init__(self):
        super().__init__()
    
duck = Bird()
print(duck.eyes) # this can now be accessed
```

```
2
```

>[!NOTE]
>We can use `super()` to access *anything* from the super class - another example is provided below

#### super() example

Sometimes, subclasses need to "override" a method to provide its own functionality. Example - in our company we have two different types of Employee - Developers and Managers.

Each employee has a salary method, which returns the yearly salary of the employee as a function of her base salary + an extra based on years of experience. It works similarly for both Manager and Developers so we put all that common functionality in a super class called `Employee`

```python
class Employee:
    def __init__(self, name, base_salary, years):
        self.name = name
        self.base_salary = base_salary
        self.years = years
        
    def salary(self):
        return self.base_salary + (self.years * 1000)
```

Developers are regular employees, so they just extend directly from `Employee` without making any modifications.

```python
class Developer(Employee):
    pass

mary = Developer('Mary Smith', 70_000, 6)
print(mary.salary())
```

```
76000
```

Managers make a little bit extra money - because they are clearly more important than the deveoplers who are actually doing the work :roll_eyes: - they make 10% more of the computed salary.

We need to rewrite the `salary()` method with a modification in the `Manager` class, but this wastes time since we are repeating code.

```python
class Manager(Employee):
    def salary(self):
        return (self.base_salary + (self.years * 1000)) * 1.1

jane = Manager('Jane Sanchez', 70_000, 6)
print(jane.salary())
```

```
83600.0
```

As we can see, with the same parameters, Jane is making more money.

Repeating the whole method again is not a great idea, though. We just need the regular salary defined in the class `Employee` and then we can add an extra 10% on top of that.

We can use `super()` in order to do this - it will allow us to reference methods implemented in parent classes.

```python
class Manager(Employee):
    def salary(self):
        return super().salary() * 1.1 # uses super()

jane = Manager('Jane Sanchez', 70_000, 6)
print(jane.salary())
```

```
83600.0
```

`super()` gives us access to the *super* class and from there we can access *anything* from that *parent* class.

## Working with Files

### Reading

We can open tiles using syntax as shown below.

```python
file = open("file.txt")
contents = file.read()
print(contents)
file.close()
```

We can simplify this code by using the `with` `as` keywords - we do not have to close the file as the `with` keyword will do this automatically.

```python
with open("file.txt") as file:
    contents = file.read()
    print(contents)
```

### Writing

We can use similar syntax to reading files to write to files.

```python
with open("file.txt", mode="w") as file:
    file.write("hello world!")
```

We need to use `"w"` as the mode so we can write to the file. This will overwrite the contents of the file.

>[!TIP]
>We can use `mode="a"` if we want to *append* data to a file

