# Python Notes

Jump to chapter: [<< 1-7 >>](#chapter-1-7)
[<< 8 >>](#chapter-8)
[<< 9 >>](#chapter-9)
[<< 10 >>](#chapter-10)
[<< 11 >>](#chapter-11)
[<< 12 >>](#chapter-12)
[<< 13 >>](#chapter-13)
  

## Some Explanations

These are backups of my notes while reading a python tutorial book.

[How to Think Like a Computer Scientist: Learning with Python 3 (RLE)](http://openbookproject.net/thinkcs/python/english3e/)  
[Source Repo of the book](https://code.launchpad.net/~thinkcspy-rle-team/thinkcspy/thinkcspy3-rle)

I don't know if it's a good book or not, but it's better than nothing anyways. And I feel pretty good up to now.

Notes are only for myself. If there is something I already know, I won't write it down.

> PS: By reading a book on a computer, I think PDF is for the hard-copy books, and HTML is for computers. It's way better to read a webpage rather than a pdf document. I don't know if we can read HTML offline on iPads, or highlight texts, make notes while reading HTML on iPads/PC. Auto adopt size and adjustable font size, just these two features completely beats PDF. It should be like "scrolling through a page" rather than "turning pages of a book". Right, nowadays there are formats for ebooks. Textbooks may should be published along with a html-like format?? That might be too expensive tho.

## Notes

<a id="chapter-1-7"></a>
### Chapter 1-7

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
### Chapter 12 Modules

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
### Chapter 13 Files

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


