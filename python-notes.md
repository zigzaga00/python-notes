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

