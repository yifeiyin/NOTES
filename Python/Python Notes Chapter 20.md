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
