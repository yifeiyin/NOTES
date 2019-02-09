Python Doc

This is more compact.

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

- `sort(dict)` `list(dist)` (will be insertion order)

- `dict( [("key1": "val1"), ("key2": "val2"), ...] )`

- `dict( key1="val1", key2="val2" )` This is easier to use when keys are strings.

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

- `_x` `__x`: Add one underscore before a var or method to make it private. Two underscores before a var/method in classes will make the var/method's name being textually replaced with `_className__x()`; Subclasses would not be able to rewrite it, it helps to avoid any name crashes or sa.

- For stuct-like data type, simply use `class SomeClass: \n pass`

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

-  Decimal Floating Point Arithmetic
    - module `decimal` provides datatype `Decimal`
