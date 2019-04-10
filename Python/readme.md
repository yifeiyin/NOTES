# Python Notes


Jump to chapter:
[1-7](#chapter-1-7) · [8](#chapter-8) · [9](#chapter-9) · [10](#chapter-10) · [11](#chapter-11) · [12](#chapter-12) · [13](#chapter-13) · [14](#chapter-14) · [15-16](#chapter-15-16) · 17 · 18 · [19](#chapter-19) · [20](#chapter-20) · [21](#chapter-21) · 22 · [23](#chapter-23) · 24 · 25 · 26 · 27

```
Chapters are skipped, for reference later:
17. PyGame
18. Recursion
22. Collections of Objects
24. Linked Lists
25. Stacks
26. Queues
27. Trees
```

[**>> Jump to Notes Part 2 (Python Tutorial on python.org) <<**](#official-python-tutorial)

## Some Explanations

These are backups of my notes while reading a python tutorials.

#### Part 1 Reference
[How to Think Like a Computer Scientist: Learning with Python 3 (RLE)](http://openbookproject.net/thinkcs/python/english3e/)
[Source Repo of the book](https://code.launchpad.net/~thinkcspy-rle-team/thinkcspy/thinkcspy3-rle)

#### Part 2 Reference
[The Python Tutorial](https://docs.python.org/3/tutorial/index.html)

#### Some Thoughts and Statistics
(File creation time: 2018.10.14) The first book or we can say tutorial, is more like an "introduction to python for programmer with some prior knowledge". It not rich enough for me, so I chose to read the tutorial from the python official site. The tutorial there certainly makes more assumptions about reader's knowledge, but with what I learned from the first book the tutorial is right for me. So I read through it spending 3 days (10±2 hours). The first book took me 4 days (13±3 hours), skipping couple chapters.

> PS: By reading a book on a computer, I think PDF is for the hard-copy books, and HTML is for computers. It's way better to read a webpage rather than a pdf document. I don't know if we can read HTML offline on iPads, or highlight texts, make notes while reading HTML on iPads/PC. Auto adopt size and adjustable font size, just these two features completely beats PDF. It should be like "scrolling through a page" rather than "turning pages of a book". Right, nowadays there are formats for ebooks. Textbooks may should be published along with a html-like format?? That might be too expensive tho.

## Notes

<a id="chapter-1-7"></a>
### 1-7. The Basics

- `type()`
    prints var's type. ex:`<class 'str'>`

- Math Operations
    - `+` `-` `*`
    - `/`  returns float
    - `//` returns int, rounding to the left
    - `**` for power
    - `%` for modulus

- Convert between types, use `int(), float(), str(),` etc.

- Get input from user, use `n = input("Prompt")`

- For-loop: `for i in range(x):`

- `asset()`

- docstrings
    ```python
    def function_one():
        """ Prints something. """ # This is docstring
        print("...")
    ```
    It will appear as help information in autocomplete.

- in Python, functions **always return values**, if none is specified, `None` is returned.

- Boolean operators: `!= == <= >= < >` `and` `or` `not`

- Conditionals:
    ```python
    if x < y:
        STATEMENTS
    elif x > y:
        STATEMENTS
    else:
        STATEMENTS
    ```
- Naming
    > I am not used to these
    - Use CamelCase for classes
    - lowercase_with_underscores for functions and variables

- Get Caller's Line Number: `import sys` `line_num = sys._getframe(1).f_lineno`

- format string: `str = "I have {0} apples.".format(num)`

- while statement:
    ```python
    while True:
        ...
    ```

- `break` `continue`

- Paired Data
    ```python
    person = ("Alex", 1998)
    people = [("...", 1999), ("...", 2000), ... ]
    for (name, year) in people:
        if year > 2000:
            ...
    ```

<a id="chapter-8"></a>
### 8. Strings

- string usages:
    ```python
    str = "string"
    str[0], str[3:5], str[3:], str[:5], str[-1]
    ```

- Strings are immutable:
    `greeting[0] = "J"   # ERROR`

- `in` and `not in` operators
    ```python
    "p"     in "apple"   # True
    ""      in "apple"   # True
    "apple" in "apple"   # True
    ```

- `find` and `split`
    split omits any white space

- Punctuation
    `import string; if letter in string.punctuation`

- format specification
    `"{0:…}".format(varA)`
    - Use `<` `^` `>` along with a number for aligments
        ex. {0:<10}
    - Use `f` for float, `x` for hexadecimal
    - Use `.2f` for float with 2 decimals


<a id="chapter-9"></a>
### 9. Tuples

- Tuples are immutable
- To create a single element tuple, add a comma in the end. ex: a = (5,)
- Use tuples to swap varibles. ex: (a, b) = (b, a)


<a id="chapter-10"></a>
### 10. Event-Driven Programming

- Keypress events
    ```python
    import turtle

    # To listen for a key, simply:
    def h1():
        tess.forward(30)

    wn.onkey(h1, "Up")

    wn.listen()
    wn.mainloop()
    ```

    - To refer to a key: use "q", "Cancel", "Up", "Down", etc. (10.1)

- keyword `global`:
    ```python
    a = 10
    def f():
        global a
        print(a)

    f()   # Will print 10
    ```
- Mouse events:
    - Mouse events on the window
        ```python
        def h1(x, y):
        tess.goto(x, y)
        wn.onclick(h1)  # Wire up a click on the window.
        wn.mainloop()
        ```

    - Mouse events on the turtle
        ```python
        def handler_for_tess(x, y):
            tess.forward(30)

        def handler_for_alex(x, y):
            alex.forward(50)

        tess.onclick(handler_for_tess)
        alex.onclick(handler_for_alex)

        wn.mainloop()
        ```
    > Ok, where is `self`? How to generalize this?

- Timer
    ```python
    def h1():
        tess.forward(100)
        tess.left(56)

    wn.ontimer(h1, 2000)
    ```
    - the timer is automatically released once fired. Therefore, we need to do this:
    ```python
    def h1():
        tess.forward(100)
        tess.left(56)
        wn.ontimer(h1, 60)

    h1()
    ```


<a id="chapter-11"></a>
### 11. Lists

- List items can be nested, they don’t have to be the same type: ```[“apple”, 200, [“today”, 10.2]]```

- Use ```len()``` ``` for item in ``` ```in, not in```

- ```+``` to concatenate, ```*``` to repeats a list a given times

- ```[a:b]``` to slice a list

- Unlike string, lists are mutable

- Use slices to perform Insertion and deletion
    ```python
    >>> a_list = ["a", "d", "f"]
    >>> a_list[1:1] = ["b", "c"]
    >>> a_list
    ['a', 'b', 'c', 'd', 'f']
    ```

- To delete, can also use ```del```. ex: ```del a_list[1:5]```

- Use ```is``` to test two variables are pointing to one memory location. If they are, we say the two vars are aliased.

- To clone a variable, use ```a=b[:]```
    ```python
    for item in list:
        item = item + 1 # doesn’t it work?
    ```

- ```enumerate()```generates paired data (on demand), ```(index, value)```
    ```python
    xs = [1, 2, 3, 4, 5]
    for (i, val) in enumerate(xs):
        xs[i] = val**2
    ```
- when passing list as argument, we are passing the pointer

- List methods
    - ```.append(newElement)```
    - ```.count(element)``` counts times of appearing
    - ```.insert(position, newElement)```
    - ```.extend(newList)``` append a list to the end
    > what’s the difference btw extend and append?
    - ```.index(element)``` indexOf (the first)
    - ```.remove(element)``` removeElement (the first one)
    - ```.reverse()```
    - ```.sort()```

- Pure function does not modify arguments

- Modifiers modifies arguments, which is called side effects

- STRING: Use ```String.split()``` to break a sentence into words. Any white spaces are the delimiter. Can also manually pass a delimiter as argument.

- ```String.join(List<String>)``` first String works as glue

- ```list()``` Type conversion, tries to make list with given things

- ```def range(from=0, to, step=1)```

- ```range()``` does not spit out a list instantly, it does it on demand.
    ```python
    >>> range(10)           # Create a lazy promise
    range(0, 10)
    >>> list(range(10))     # Call in the promise, to produce a list.
    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    ```

- To visit Nested list or Matrix: ```Val = a_list[2][3]```


<a id="chapter-12"></a>
### 12. Modules

- Module `random`:
    ```python
    import random
    random_black_box = random.Random()
    ```
    - `.randrange(lowerBound, higherBound, step)`, include lowerBound, exclude higherBound.
    - `.random()` generates a number `[0.0, 1.0)`
    - `shuffle(list)` shuffles a list.
    - explicit seeding: `random.Random(seed)`

- Module `time`:
    ```python
    import time
    time_since_program_starts = time.clock()
    # it returns a float number in seconds
    ```

- Module `math`:
    ```python
    import math
    math.pi
    math.e
    math.sqrt(number)
    math.redians(90)
    math.sin(rad)
    math.asin(1.0)   # arcsin
    ```
    - Notice: We don't need to create any objects, becuase math operations does not depend on any "states". They are just functions.


- Creating Own Modules
    ```python
    ### seqtools.py
    example_constant = 10
    def remove_at(pos, seq):
        return seq[:pos] + seq[pos+1:]
    .
    ### main.py
    import seqtools
    s = "a string!"
    seqtools.remove_at(4, s)
    print(seqtools.example_constant)
    ```
    - Notice: In the import statement, do not include ".py"
    - In Python: One file, one module. The file name is the module name. (excluding the .py)

- Scope and Loopup Rules

    - precedence rules: Local Scope -> Global Scope -> Built-in Scope

- `import` statement variants
    - `import math`
    - `import math as m`
    - `from math import cos, sin, sqrt`
    - `from math import *`
    - Note: we can import things within a function


<a id="chapter-13"></a>
### 13. Files

- Creating a File Handle
    ```python
    file = open("fileName.ext", "w|r|...")
    file.close()
    ```

    - > Note: The variable file is not actual file on the disk. Their relationship is like the one between a remote and the TV.

    - mode write `"w"`:
        If there is no existing file, it will be created; if there is one, it will be cleared.

    - mode read `"r"`: (default)
        - Reads lines from an existing file. Trying opening a non-existing file will generates an error.
        - `.readline()` acquires a line. The `\n` is reserved at the end of the string. Therefore, to test if we reached the end, simply use `len(newLine)`.
        - `.readlines()` gets a list of strings containing the lines in the file.

    - For binary files such as pictures, zip files, use mode "rb" or "wb" where *b* is for binary. The result variable will be type `bytes`.


- The directory is defaulted to be the same as the program. Explictly say the absulote path when neccessary.

- An example using urllib.request to retrieve content from the web.
    > socket: One end of a connection allowing one to read and write information to or from another computer.
    ```python
    import urllib.request

    def retrieve_page(url):
        """ Retrieve the contents of a web page.
            The contents is converted to a string before returning it.
        """
        my_socket = urllib.request.urlopen(url)
        dta = str(my_socket.readall())
        my_socket.close()
        return dta

    the_text = retrieve_page("http://xml.resource.org/public/rfc/txt/rfc793.txt")
    print(the_text)
    ```


<a id="chapter-14"></a>
### 14. List Algorithms

- `string.maketrans("ABC", "abc")` *trans* is for translate. It substitutes characters in avg1 with the corresponding char in avg2.

- Test-driven development (TDD)

- Binary Search
    - Use ROI (region of interest), lb (lower bound), ub (uppper bound).

- Removing adjacent duplicates from a list

- Merging sorted lists


<a id="chapter-15-16"></a>
### 15-16. Classes and Objects

- Python is an object-oriented programming language, which means that it has features which support object-oriented programming (OOP).

- `__init__` will be called after an instance being created.
    ```python
    class ClassName:
        """docstring"""

        def __init__(self):
            """docstring"""
            self.x = 0
            self.y = 0
    ```

- `__str__` will be called whenever it needs to be converted to string. ex. `print(...)`
    ```python
        def __str__(self):
            return "({0}, {1})".format(self.x, self.y)
    ```

- **Shallow Equality** and **Deep Equality**. Shallow equality only compares the references. Deep equality compares the content of the obejcts.

- **Shallow Copying** and **Deep Copying**. Module `copy` provides `copy()` and `deepcopy()`.
    - `copy.copy(obj)` does shallow copy, it creates a new object and initilize it with the same data. However, if there is any pointers, they still points to the same location.
    - `copy.deepcopy()` does deep copy. Any embedded objects are created if needed.


<a id="chapter-19"></a>
### 19. Exceptions

```python
try:
    ...
except:
    ...
finally:
    ...
```

- `try ... except ...` handles the error

- `try ... finally ...` does not handle the error, the program still crashes, but the "finally" block is executed before crashing.

- `except RuntimeError:`
- `except (RuntimeError, TypeError, NameError):`
- More refer to (Python Documentation)[https://docs.python.org/3/tutorial/errors.html]


<a id="chapter-20"></a>
### 20. Dictionaries

```python
  dict = {}
  dict["one"] = "uno"
  dict["two"] = "dos"
  eng2sp = {"one": "uno", "two": "dos", "three": "tres"}
  print(eng2sp["two"])
```

- Key and Value. Key can be any immutable types, value can be any type.

- `del dict["pears"]`

- `len(dict)`

- `for k in eng2sp.keys():`
    - The `.keys()` can be ommited. Simply use `for k in eng2sp:`

- `list(eng2sp.values())`

- `list(eng2sp.items())` generates a list of tuples, (key, value).

- `for (key, val) in eng2sp.items():`

- Looking up a non-existing key in a dictionary causes an error. Use `in` or `not in` to test first.

- `in` and `not in`: `if "one" in eng2sp: ...` `if "two" not in eng2sp: ...`

- Use `.copy()` and `.deepcopy()` in module copy for non-alias copying.

- `.get(key, defaultValueToReturn)` spits out a default value if the key in not in the dictionary.


<a id="chapter-21"></a>
### 21. More OOP

- Operator Overloads
    - `+`: `def __add__(self, other):`
    - `-`: `def __sub__(self, other):`
    - `*`: `def __mul__(self, other):` If operand on the left is the class type.
    - `*`: `def __rmul__(self, other):` If operand on the left is the class type.

    - `==`: `__eq__`
    - `<=`: `__le__`
    - `>=`: `__ge__`
    - `>`: `__gt__`
    - `<`: `__lt__`
    - `!=`: `__ne__`

    - Write a `cmp(self, other)` to house the compare logic. By convention, a comparison method takes two parameters, self and other, and returns 1 if the first object is greater, -1 if the second object is greater, and 0 if they are equal to each other.

    - And simply overload the operators by:
    ```python
    def __eq__(self, other):
        return self.cmp(other) == 0

    def __le__(self, other):
        return self.cmp(other) <= 0

    def __ge__(self, other):
        return self.cmp(other) >= 0

    def __gt__(self, other):
        return self.cmp(other) > 0

    def __lt__(self, other):
        return self.cmp(other) < 0

    def __ne__(self, other):
        return self.cmp(other) != 0
    ```

- Python deals very well with polymorphism.

- Duck typing:

    - > Pythonic programming style that determines an object's type by inspection of its method or attribute signature rather than by explicit relationship to some type object ("If it looks like a duck and quacks like a duck, it must be a duck.") By emphasizing interfaces rather than specific types, well-designed code improves its flexibility by allowing polymorphic substitution. Duck-typing avoids tests using type() or isinstance(). Instead, it typically employs the EAFP (Easier to Ask Forgiveness than Permission) style of programming.


<a id="chapter-23"></a>
### 23. Inheritance

```python
class Subclass(ParentClass):
    ...
```

- To call parental methods: ```ParentClass.method(self)```, example:
```python
class Hand(Deck)
    ...
    def __str__(self):
        s = "Hand " + self.name
        if self.is_empty(): s += " is empty\n"
        else: s += " contains\n"
        return s + Deck.__str__(self)
```







```
# ------------------------------------------------------------ #

# ------------------------------------------------------------ #

   ________  ________  ________  _________         _______
  |\   __  \|\   __  \|\   __  \|\___   ___\      /  ___  \
  \ \  \|\  \ \  \|\  \ \  \|\  \|___ \  \_|     /__/|_/  /|
   \ \   ____\ \   __  \ \   _  _\   \ \  \      |__|//  / /
    \ \  \___|\ \  \ \  \ \  \\  \|   \ \  \         /  /_/__
     \ \__\    \ \__\ \__\ \__\\ _\    \ \__\       |\________\
      \|__|     \|__|\|__|\|__|\|__|    \|__|        \|_______|


# ------------------------------------------------------------ #

# ------------------------------------------------------------ #
```



<a id="official-python-tutorial"></a>

# Part 2 - Notes from the Official Python Tutorial

### 3

- In interactive mode, `_` represents last result. (3.1.1)

- Use `\` in `"""..."""` at the end of line to exclude the new line character.

- `'abc' 'def' == 'abcdef'` Use this to break down long sentence into multiple lines.

### 4. Control Flow Tools

- Use `for w in words[:]:` to make a copy first, if any modification on the list happens.

- `else` in loops. `break` is executed when the list is exhausted, or the condition becomes false, **not** when exited using `break`.

- `else` also goes with `try` where no exceptions would execute it.

- `pass`: placeholder for syntax

#### Functions

- In function calls, there are keyword arguments and positional arguments. All keywords arguments must follow positional arguments.

- `*name` and `**name`. `*name` receives a tuple of positional arguments (arg1, arg2, ...). `**name` receives a dictionary of arguments (keyword:arg). `*name` has to go before `**name`.

- Arbitrary Argument List
    ```python
    >>> def concat(*args, sep="/"):
    ...     return sep.join(args)
    ...
    >>> concat("earth", "mars", "venus")
    'earth/mars/venus'
    >>> concat("earth", "mars", "venus", sep=".")
    'earth.mars.venus'
    ```

- Unpacking Argument Lists
    ```python
    args = [3, 6]
    for a in range(*args):
    """ is equivlent to """
    for a in range(3, 6):
    ```
    ```python
    args = {"a": 1, "b": 2, "c": 3}
    f(**args)
    """ is equivlent to """
    f(a=1, b=2, c=3)
    ```

- Lambda Expression
    ```python
    lambda x: x+...
    """ is equivlent to """
    f(x) where def f(x): return x+...
    ```

- Docstring
    ```python
    def f():
        """Brief summary, full sentence.

        Long, detailed description here.
        """
    ```
    - Use `f.__doc__` to get the docstring.

- Function Annotations
    ```python
    def f(ham: <<1>>, eggs: <<2>> = 'eggs') -> <<3>>:
        pass
    ```
    - In `<<1>> <<2>> <<3>>`, they can be string, can be class name, or any expression. It's up to the developer what goes there.

    - Use `f.__annotation__` to get the annotation.


### 5. Data Structures

#### List

- Using list as stacks: `.append(newVal)` `.pop() -> element`

- Using list as queues:
    ```python
    from collections import deque
    queue = queue(["23", "12", "23"])
    queue.append("vvv")
    a = queue.popleft()
    ```

- List Comprehensions
    ```python
    squares = []
    for x in range(10):
        squares.append(x**2)
    """ is equivlent to """
    squares = list(map(lambda x: x**2, range(10)))
    """ is equivlent to """
    squares = [x**2 for x in range(10)]
    ```
    ```python
    squares = [<<exp1(vars)>> <<exp2>>]
    <<exp2>> could be:
    """for b in a for <<exp1(vars)>> in b if condition"""
    """^--------^ ^---------------^ ^----------^"""
    """ is equivlent to """
    """ for b in a:
            for <<exp1(vars)>> in b:
                if condition:
                    squares.append(exp1(vars))
    """
    ```

- `del` can be also used on a variable. `del a` creates a null pointer.

#### Set
- To create: `basket = {"apple", "orange"}`
- To create an empty set: `basket = set()`, `{}` is for dictionary.
- Any duplicated items will be removed.
- Can also use `set("string")` to create a set `{'s', 't', ...}`.
- Use `-` `|` `&` `^` to perform difference, union, intersection, union exclude intersection.
- Also supports set comprehensions: `a = {x for x in 'abracadabra' if x not in 'abc'}`

#### Dictonaries

- The key can be any immutable type, such as int, string, tuple (containing int/string/tuple only).

-`sort(dict)` `list(dist)` (will be insertion order)

- `dict( [("key1": "val1"), ("key2": "val2"), ...] )`

-`dict( key1="val1", key2="val2" )` This is easier to use when keys are strings.

#### Looping Techniques

- `zip()`
    ```python
    questions = ['name', 'quest', 'favorite color']
answers = ['lancelot', 'the holy grail', 'blue']
for q, a in zip(questions, answers):
    print('What is your {0}?  It is {1}.'.format(q, a))
    ```

- `reversed(...)` ex`reversed(range(1, 10))`

#### More on Conditions

- Comparisions cna be chained. ` a < b < c`

### 6. Modules

- When a module is imported, it will be run.

- Use `__name__` to get the module name.

- Compiled Python Files (6.1.3), Using `-O` `-OO` to optimize modules.

- `sys.ps1` and `sys.ps2` define the primary and secondary prompts. `sys.path` defines the interpreter's search path for modules.

- `dir()` lists out names that have been defined. `dir(module)` lists out names that have been defined in the module. Use `import buildins, dir(buildins)` for all buildin names.

#### Packages

`import a.b.c`
```
sound/                          Top-level package
      __init__.py               Initialize the sound package
      formats/                  Subpackage for file format conversions
              __init__.py
              wavread.py
              ...
      effects/                  Subpackage for sound effects
              __init__.py
              echo.py
              ...
      ...
```
- Import individual module from a package: `import sound.effects.echo`. However, it must be refered with its full name. Or use `from ... import ...` instead.

- `__all__` in the `__init__.py` defines what is imported with `import *`.

- Relative path: `from . import ...` `from .. import ...` etc.

### 7 Input and Output

- Use f or F before a string to format python expression in brackets: `f"Results of the {year} {event}"`. For more, see ref guide 6.1.3.1.

- In `"{0:}".format()`, the number 0 can be omitted.
```
"{food}".format(food="spam")

table = {'Sjoerd': 4127, 'Jack': 4098, 'Dcab': 8637678}
print('Jack: {0[Jack]:d}; Sjoerd: {0[Sjoerd]:d}; '
      'Dcab: {0[Dcab]:d}'.format(table))

table = {'Sjoerd': 4127, 'Jack': 4098, 'Dcab': 8637678}
print('Jack: {Jack:d}; Sjoerd: {Sjoerd:d}; Dcab: {Dcab:d}'.format(**table))
```
- For more about `.format()`, see ref guide 6.3.1.

- `str() & .__str__` `repr() & .__repr__` `eval()`

- buildin func `vars()` returns a dictionary containing all local vars.

- `str.rjust()` `.ljust()` `.center()` `.zfill()` z for zero

#### Files

- `"r+"` for both reading and writing.

- `f.tell()` gives the current position in the file.

- `f.seek(offset, from_what)` changes the position.

- `json`

### 8. Errors and Exceptions

- `Exception('...', '...')` args are stored in .args. They are printed as the last part of the message.

- `raise ValueError` `raise ValueError()` `raise`

- Use `with open("myfile.txt") as f:` for opening files.

### 9. Classes

- Scopes `nonlocal` `global`
    - `global` makes the name belongs to the module's global name list.
    - `nonlocal` makes the name belongs to the list which is owned by "one layer outer" of the current scope, for example in nested functions.
    - Without these keywords, outer names are read only. Attempts of assigning values will create a new variable.

- `_x` `__x`: Add one underscore before a var or method to make it private. Two underscores before a var/method in classes will make the var/method's name being textually replaced with `_className__x()`; Subclasses would not be able to rewrite it, it helps to avoid any name crashes.

- For struct-like data type, simply use `class SomeClass: \n pass`

- Iterators: `__iter__` `__next__`
    - To make an object conforts `for ... in ...`, the object needs to implement `__iter__(self)`. This function should return an object which defines `__next__(self)`. The `__next__()` returns the next object and raise a `StopIteration` exception when reaches the end.
    - If the object defines both `__iter__` and `__next__` the *iter* can just return `self`.


- Generators:
    ```python
    def reverse(data):
    for index in range(len(data)-1, -1, -1):
        yield data[index]
    ```
    - Use `yield` to return value. It automatically generates iterators.


- Generator Expressions, it is similar to list comprehensions, but this uses round brackets instead of square brackets. examples:
    ```python
    sum(i*i for i in range(10))                 # sum of squares
    ```


    xvec = [10, 20, 30]
    yvec = [7, 5, 3]
    sum(x*y for x,y in zip(xvec, yvec))         # dot product


    from math import pi, sin
    sine_table = {x: sin(x*pi/180) for x in range(0, 91)}

    unique_words = set(word  for line in page  for word in line.split())

    valedictorian = max((student.gpa, student.name) for student in graduates)

    data = 'golf'
    list(data[i] for i in range(len(data)-1, -1, -1))
    ```

### 10. Standard Library

- Module `os`
    - os for Operating System
    - `getcwd()` returns the current working directory
    - `chdir("...")` changes the current working directory
    - `system("...")` executes the command in the system shell

- Module `shutil`
    - shutil for shell utility
    - `copyfile("from", "to")`
    - `move("from", "to")`

- Others modules about files and path
    - Module `glob` for file wildcards. ex `glob.glob("*.py")`
    - Module `pathlib` for high-level path objects.

- Module `sys`
    - Command Line Arguments: `import sys` `sys.argv` contains the list of arguments.
    - For C-style `getopt()`, use `getopt`.
    - For more powerful and flexible command line processing tool, use `argparse`.
    - has attributes for *stdin*, *stdout* and *stderr*.
    - `stderr.write("...")`
    - `exit()`

- Module `re`

    - sometimes for simple capabilities, use string methods such as `"abc".replace("from", "to")`.

- Mathematics
    - `math` gives underlying C library functions.
    - `random` provides tools for making random selections.
        - `choice(['apple', 'pear', 'banana'])`
        - `sample(range(100), 10)` sampling without replacement
        - `random()`
        - `randrange(6)`
    - `statistics`
        - `mean(data)`
        - `median(data)`
        - `variance(data)`

    - `SciPy` has more modules for numerical computations.

- Internet Access
    - `urllib.request` `smtplib`
    ```python
    from urllib.request import urlopen
    with urlopen('http://tycho.usno.navy.mil/cgi-bin/timer.pl') as response:
        for line in response:
            line = line.decode('utf-8')  # Decoding the binary data to text.
            if 'EST' in line or 'EDT' in line:  # look for Eastern Time
                print(line)

    import smtplib
    server = smtplib.SMTP('localhost')
    server.sendmail('soothsayer@example.org', 'jcaesar@example.org',
    """To: jcaesar@example.org
    From: soothsayer@example.org

    Beware the Ides of March.
    """)
    server.quit()
    ```

- Module `datetime`

- Data Compression

    - `zlib` `gzip` `bz2` `lzma` `zipfile` `tarfile`

- Module `timeit`
    - ex `timeit.Timer('a = 1', 'b = a').timeit()`
    - Modules `profile` and `pstats` provides tools for identifying time cretical sections in larger blocks of code.

- Quality Control
    - `doctest`
    - `unittest`

- Others Modules
    - `xmlrpc.client` `xmlrpc.server` for remote procedure calls.
    - `smtplib` `poplib` for sending and receiving emails.
    - `email` for building and decoding complex message structures.
    - `json` `csv` `xml.etree.ElementTree, xml.dom, xml.sax` for data interchange.
    - `sqlite3` for SQLitedatabase library.
    - `gettext` `locale` `codecs` for internationalization.


### 11. More about the Standard Library

- Output Formatting
    - `reprlib` provides a version of repr() customized for abbreviated displays of larger containers.
    - `pprint`, pretty print, offers `pprint()` which prints out more readable content than the build-in `print()`.
    - `textwrap` formats paragraphs to a certain width.
    - `locale` accesses a database of culture specific data formats, such as number grouping. ex `1,000,000`

- Templating
    ```python
    from string import Template
    t = Template("Here is $arg1")
    t.substitute(arg1="substitution")
    ```

- Working with Binary Data Record Layouts

- Multi-threading

- Logging

- Weak References

- Tools for Working with Lists

    - `array` `collections` `bisect` `heapq`

- Decimal Floating Point Arithmetic

    - module `decimal` provides datatype `Decimal`

