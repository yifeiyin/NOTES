### Chapter 12 Modules

- Module `random`:
    ```python
    import random
    random_black_box = random.Random()
    ```

    - `.randrange(lowerBound, higherBound, step)`, include lowerBound, exclude higherBound.

    - `.random()` generates a number [0.0, 1.0)

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
    - precedence rules:
        Local Scope -> Global Scope -> Built-in Scope


- `import` statement variants
    - `import math`
    - `import math as m`
    - `from math import cos, sin, sqrt`
    - `from math import *`
    - Note: we can import things within a function






