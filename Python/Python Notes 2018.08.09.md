# Python Notes 2018.08.09

How to Think Like a Computer Scientist: Learning with Python 3 by Peter Wentworth, Jeffrey Elkner, Allen B. Downey and Chris Meyers


### 8. Strings

- string usages: 
    ```
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


### 9. Tuples

- Tuples are immutable
- To create a single element tuple, add a comma in the end. ex: a = (5,)
- Use tuples to swap varibles. ex: (a, b) = (b, a)


### 10. Event-Driven Programming

- Keypress events
    ```
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
    ```
    a = 10
    def f():
        global a
        print(a)

    f()   # Will print 10
    ```




