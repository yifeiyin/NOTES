JavaScript Notes
================

> 2019 March 10
> Reading javascript.info

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


