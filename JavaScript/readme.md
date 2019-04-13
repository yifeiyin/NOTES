JavaScript Notes
================

> 2019 March 10
> Reading javascript.info

<!-- TOC -->

## Table of Contents
1. [JavaScript Fundamentals](#javascript-fundamentals)
    1. [Preliminaries](#preliminaries)
    1. [Variables, Constants](#variables,-constants)
    1. [Primitive Data Types](#primitive-data-types)
    1. [Type Conversions](#type-conversions)
    1. [Operators](#operators)
    1. [Comparisons](#comparisons)
    1. [Interactions](#interactions)
    1. [Conditions](#conditions)
    1. [Logical Opeartors](#logical-opeartors)
    1. [Loops](#loops)
    1. [Switch](#switch)
    1. [Functions](#functions)
1. [Code Quality](#code-quality)
    1. [Debugging in Chrome](#debugging-in-chrome)
    1. [Coding Style](#coding-style)
    1. [Automated Testing](#automated-testing)
    1. [Polyfills](#polyfills)
1. [Objects](#objects)
    1. [Basics](#basics)
    1. [Garbage Collection](#garbage-collection)
    1. [Symbol Type](#symbol-type)
    1. [Object methods, "this"](#object-methods,-"this")
    1. [Object to Primitive Conversion](#object-to-primitive-conversion)
    1. [Constructor, "new" operator](#constructor,-"new"-operator)
1. [Data Types](#data-types)
    1. [Methods of Primitives](#methods-of-primitives)
    1. [Numbers](#numbers)
        1. [How Number Looks Like](#how-number-looks-like)
        1. [Number Object Methods](#number-object-methods)
        1. [`Math` Rounding Methods](#`math`-rounding-methods)
        1. [Number Related Functions](#number-related-functions)
        1. [Other Math Functions](#other-math-functions)

<!-- /TOC -->



## JavaScript Fundamentals

### Preliminaries
- `<script src='...'> </script>`
    - will load outside script and ingore content inside the tag

- Semicolons
    - Can be omitted in most cases for standalone statements (automatic semicolon insertion)
    - Nonetheless, putting semicolons ALL THE TIME is recommended

- Comments
    - C-Style Comment: `// ...` `/* ... */`

- "use strict"
    - Add `"use strict";` at the beginning of the script. single quotes also work
    - Putting it at the begining of functions also works in some cases
    - Cannot go back
    - Browser console does not use strict by default, use this instead
    ```js
    (function() {
        'use strict';
        // code here
    })()
    ```

### Variables, Constants
- Variables
    - use `let` keyword
    ```js
    let message;
    message = 'Hello';
    alert(message);

    let msg2 = 'Hello';
    let a = 10, b = 20, c = "world";
    ```
    - `var` is the old school way of `let`
    - Naming: contains only `1-9 a-z A-Z $ _`. Must not start with a digit
    - Case matters, Use camelCase

- Constants
    - use `const` keyword
    - can be assigned on demand; cannot be re-assigned
    - use all upper letters for "hard to remember" constants

### Primitive Data Types
- JS is dynamically typed. Can change a var's type
- Number
    - with decimal places or without
    - Also includes `Infinity, -Infinity, NaN`
- String
    - Double quotes and single quotes are the same
    - **Backticks** allow evaluation exists, use `${...}`: `alert( `1 + 1 = ${1 + 1}` );`
- Boolean
    - `true` `false`
- "null"
    - Represent a reference to a non-existing object
- "undefined"
    - Repersent a declared but not assigned variable value
    - Use null for empty values, only use undefined for checking
- Others
    - `object` `symbol` will be mention later

- `typeof`
    - Can be used as a function or a operator: `typeof x; typeof(x);`

### Type Conversions
- To String: `String(...)`
- To Number: `Number(...)`
    | value        | Result of Number()            |
    | ------------ | ----------------------------- |
    | undefined    | NaN                           |
    | null         | 0                             |
    | true/false   | 1 or 0                        |
    | string       | Whitespaces are striped, NaN if error |

- Almost all math operations will convert values to numbers, **besides** `+`
    ```js
    1 + '2' // '12'
    '1' + 2 // '12'
    ```
- To Boolean: `Boolean(...)`
    - `'(empty string)', 0, null, undefined, NaN` are false
    - all others are true

### Operators
- unary, binary, operand
- Binary `+`
    - When one of the operand is string: will convert the other one to string and concatenate
    - Else, will convert all to numbers and do math addition
- Unary `+`
    - Will convert the operand to numbers, equivalent to `Number(...)`
    ```r
    let apples = "2";
    let oranges = "3";

    // both values converted to numbers before the binary plus
    alert( +apples + +oranges ); // 5
    ```

- Supports Chain Assignments

- `%` Remainder
- `**` Exponential
- `++` `--`

- Bitwise Operators
    - and `&`
    - or `|`
    - xor `^`
    - not `~`
    - left shift `<<`
    - right shift `>>`
    - zero-fill right shift `>>>`

- `+= -= etc`
- Command Operator: just like C

### Comparisons
- `> < >= <= == !=`
    - For strings, it is comparing alphabetical order (more strictly, unicode order)
    - Will convert values to numbers
    - `==` treats undefined and null differently: they only equal to themselves, nothing else

- `===`
    - Compare without type conversions
    - `null === undefined` will be false too

### Interactions
- alert
    - `alert(message);`
- prompt
    - `result = prompt(title[, default]);`
    - if cancelled, will get null
    - For the sake of looking good in IE, always provide default
- confirm
    - `result = confirm(question);`
    - Will get true/false

### Conditions
- `if (...)` `else` `else if`
- `cond? block1 : block2`

### Logical Opeartors
- Will use short circuit evaluation
- `||` OR
    - Also finds the first truthy value
- `&&` AND
    - Also finds the first falsy value
- `!` NOT
    - `!! ...` <-> `Boolean(...)`

### Loops
- `while` `do ... while`
- `for(..; ..; ..)`
- `continue` `break`
- `break <labelName>`: add a labelName in front of the loop statement
- `continue <labelName>`: same thing

### Switch
- Takes any type for the switch argument
- Does not supply break statement, need to write it out
- CASE MATTERS, works like `===`

### Functions
- Functions *Declaration*
    ```js
    function functionName(arg1, arg2 = "default value") {
        return 1;
        return; // returning undefined
        // No return statement will also return undefined
    }
    ```
- If not all arguments are provided, the missing parameter will be undefined

- Function *Expression*
    ```js
    let functionName = function(parameters, here) { ... };
    ```
- When to print a function expression, the code inside the function will be printed
- **Important Example**
    ```js
    function ask(question, yes, no) {
      if (confirm(question)) yes()
      else no();
    }

    ask(
      "Do you agree?",
      function() { alert("You agreed."); },
      function() { alert("You canceled the execution."); }
    );
    ```

- Function **Definitions** Can appears AFTER usage, as long as they are defined
- Arrow Functions
    ```js
    let plus = function(x, y) { return x; };
    // Simply to:
    let plus = (x, y) => x + y;
    //         |<----------->|

    // If no parameters, leave the parehtheses empty
    let hello = () => alert("hello");

    // For multi-line functions, use curly braces and return statements
    let sum = (a, b) => {
        let result = a + b;
        return result;
    }
    ```

## Code Quality
### Debugging in Chrome
- Chrome environment
- `debugger;`
- `console.log(msg);`
- break points, continue to here, watch expressions, etc

### Coding Style
- Always use semicolon
- Use spaces correctly
- Put helper functions at the end
- There are linters available

### Automated Testing
- BDD: Bahavior Driven Development: Write test cases first, then write code
- Mocha: Testing Framework, Sample code:
    ```js
    describe("pow", function() {

      it("raises to n-th power", function() {
        assert.equal(pow(2, 3), 8);
      });

    });
    ```
- Other Frameworks:
    - Chai: provide different kinds of assertions
    - Sinon: a library to spy over functions

### Polyfills
- Not all engines has all features
- Babel, transpiler




## Objects

### Basics
- Created with `let a = { "key, type string or symbol": "value, any type" };`
    - Also, less used form `let a = new Object();`
- Property values:
    - Add using `a.name = "Jack";`
    - Remove using `delete a.name;`
- Multiword property names must be quoted: `let b = { key1: 1, "key 2": 2 };`
- Square Notation: Also, this allows to use different keys on demand
    ```js
    let user = {};
    user["likes birds"] = true;

    let key = "likes birds";
    alert(user[key]);
    ```
- Computed Properties
    ```js
    let fruit = prompt("Which fruit to buy?", "apple");

    let bag = {
        [fruit]: 5,
    //  ^-----^
    };
    ```

- Property Value Shorthand
    ```js
    let user = {
        name,       // Same as   name: name
        age = 30,
        gender,     // Same as   gender: gender
    };
    ```

- Property Existence Check
    - Trying access property that is not set will get `undefined`
    - Check use `=== undefined` or `key in object`

- for-in loop
    ```js
    for (let key in object) {
        ...
    }
    ```
- Order of Keys
    - Integer properties are ordered increasingly. Others are ordered by creation order
    - Integer properties are the strings that can be converted to-and-from int without change
    - Add a "+" before the int in the string can make it not become integer property

- "Mutable vs Immutable": (Are these the right vocabulary in js?)
    - Primitive types are immutable, copied as a whole
    - Objects are copied **by reference**
- Equal Signs on Objects
    - `===` and `==` has no difference when used on objects:
    - They both check if two references are pointing at the same object
- Cloning
    - Use a for loop: `let src = {...}; let clone = {}; for (let k in src) { clone[k] = src[k]; }`
    - Use `Object.assign`: 
        - Of form `Object.assign(dest[, src1, src2, src3...])`, returns `dest`
        - Overwrites existing properties
        - `let clone = Object.assign({}, user);`
        - `Object.assign(clone, user);`
    - For deep cloning, use library `lodash`, method name `_.cloneDeep(obj)`

### Garbage Collection
- JavaScript is smart about garbage collection: circular references are taken care of

### Symbol Type
- Symbol value repersents a unique identifier, will never be the same
    - Can give it a name for debugging purpose: `let s = symbol("name here");`
    - Can be used for object keys so that they will not collide with customized keys
    - Note: Use square brackets in object literal: `let id = Symbol(); let user = { name: "A", [id]: 123 };`
- Symbols are skipped in for...in loop
    - But `Object.assign` will keep the symbols

- Global Symbols
    - Use this feature when: different parts of the application want to have the "same" symbol by name
    - Called "global symbol registry", these symbols are called "global symbols"
    - To create or read a symbol, use `Symbol.for(key)`. If not exists, will create and return; if exists, will returns it
    - Use `Symbol.keyFor(symbol)` to do the reverse: get the name by supplying the symbol; Non-global symbols will not work

- System Symbols
    - Example: `Symbol.toPrimitive` `Symbol.iterator`
    - Will use later

- Other things
    - `Object.getOwnPropertySymbols(obj)`
    - `Reflect.ownKeys(obj)`

### Object methods, "this"
- Adding methods to objects:
    ```js
    let user = {
        sayHi: function() {
            alert("hi");
        },
        name: "Name",

        // Short Hand
        sayHi2() {
            alert("hi");
        }
    }
    ```
- To get the property of the object itself, use keyword `this`
- Technically, can use the outside variable name to reference self, too (But don't do it)
- `this` has no value until the function is called
- When `this` is unbounded, ie called outside of an object, it will behave differently without "use strict"
- Note:
    ```js
    (user.name == "John" ? user.hi : user.bye)(); // Error!
    ```
    - Because `user.hi` is outside, when it is called, no objects are provided
    - the dot `.` returns not a function, but a value of the special *Reference Type*
    - The only way to get it called correctly is to use `obj.method()` or `obj['method']()`
- Arrow functions takes `this` from the outer scope

### Object to Primitive Conversion
- Evaluated as:
    - bool: true; objects are always true
    - numberic; use when subtract objects or apply math functions
    - string; happens like `alert(obj)`

- Hints
    - The object may be used by "ToPrimitive" algorithm to convert it to other types
    - "string"
    - "number" (greater than, less than are using this too)
    - "default" (happens when the operator is not sure what type to expect) (usually implemented the same as "number")

- To do the conversion, it tries to find these methods
    - Call `obj[Symbol.toPrimitive](hint)` if the method exists
    - O/w, if hint is "string", call `obj.toString()` `obj.valueOf()` if exists
    - O/w, (hint is "number" or "default"), call `obj.valueOf()` `obj.toString()` if exists

- For exmaple:
    ```js
    let user = {
      name: "John",
      money: 1000,

      [Symbol.toPrimitive](hint) {
        alert(`hint: ${hint}`);
        return hint == "string" ? `{name: "${this.name}"}` : this.money;
      }
    };
    ```

- The `ToPrimitive` method does not need to return the requested type, but it has to be a primitive type. Any additional (build-in) type conversion methods will apply if necessary.

- In practice, it is often enough to implement only `obj.toString()` for debugging purpose

### Constructor, "new" operator
    ```js
    function User(name) {
        // this = {};    -- think of it this way
        this.name = name;
        this.isAdmin = false;
        // return this;    -- think of it this way
    }

    let user = new User("Jack"); // (using `new`)
    ```
- Syntax-wise, the name of the constructor starts with a capital letter
- Syntax-wise, the parentheses after `new` does not to be there if there is not arguments, but don't do it


- `new` makes the following happens
    - Create an empty object and assigned it to `this`
    - Function body executes, usually adding/modifying properties to `this`
    - return `this`

- For creating more complex objects, can use this
    ```js
    let user = new function() {
        this.name = "John";
        this.isAdmin = false;
        // ... More complex statements here ...
    }
    ```
    - Explanation: `function() { ... }` creates a function; `new` operator adds the two implicit lines (see notes above); and the function gets correctly called

- (Extra) Dual-syntax constructor: `new.target`
    - Being used when want to make a function work with and without `new` operator (used in librarys)
    - A special property called `new.target` is set to the function itself when it is called using `new`, empty otherwise
    - In the function body, simply check `new.target` and do corresponding things

- Return statements in constructors
    - (Of course, it usually does not have a return statement)
    - If `return` is called with a object, the object is returned
    - If `return` is called with a primitive, the primitive is ingored and `this` object is returned



## Data Types

### Methods of Primitives
- Motivation: want primitive to have methods for easy access, but still need them to be light
- Solution: when call method on a primitive, an "object wrapper" will be created then be destroyed.
- The object for each primitive type are called: `String`, `Number`, `Boolean` and `Symbol`.
    - For exmaple: `str.toUpperCase()` `num.toFixed(2)`
- NOTES
    - `Number(...); Boolean(...); etc` are fine to use
    - `new Number(...); Boolean(...); etc` do NOT use. Do not try to create the temporary object wrapper object, confusing things will happen (ex. `let zero = new Number(0); zero == true; because it is an object`)
    - `null` and `undefined` have no methods
    - the JavaScript engine will optimize the process so no temporary object will be created

### Numbers
#### How Number Looks Like
- Scientific notation: `3.2e100`, `6e-3`
- Hex, binary, octal numbers: `0xff 0xFF` `0b1111 0B1010` `0o4567 0O77621`

#### Number Object Methods
- Note: To use methods directly on a number, use `(123).toString(36)` or `123..toString(2)`
- `.toString(base)`
    - Default is `10`, valid values are `2 .. 10`
    - Use `num.toString(2)` for debug purpose
    - Use `num.toString(36)` for making unique identifier (will use 0-1, A-Z)
- `.toFixed(n)`
    - Returns a string with number rounded to n-th decimal, with 0 added if necessary

#### `Math` Rounding Methods
- `Math.floor` makes it smaller
- `Math.ceil` makes it bigger
- `Math.round` rounds
- `Math.trunc` getting rid of decimal part, not supported by IE

#### Number Related Functions
- `isNaN(value)`
- `isFinite(value)`
- (to strictly test numbers check out `Object.is(a, b)`)
- `parseInt(str)` `parseFloat(str)`
    - They will try to read numbers as much as possible
    - Supports 2nd argument: `parseInt(str, radix)` radix = base to parse in

#### Other Math Functions
- `Math.random()` returns number in `[0, 1)`
- `Math.max(...)` `Math.min(...)`
- `Math.pow(base, power)`

