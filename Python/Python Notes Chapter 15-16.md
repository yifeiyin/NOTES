### Chapter 15-16 Classes and Objects

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

