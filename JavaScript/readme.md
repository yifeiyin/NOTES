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
    1. [Strings](#strings)
        1. [Basic Accessing](#basic-accessing)
        1. [Finding, Testing, Slicing](#finding,-testing,-slicing)
        1. [Unicode Encoding](#unicode-encoding)
    1. [Arrays](#arrays)
        1. [Adding, Accessing, Finding Methods](#adding,-accessing,-finding-methods)
        1. [Transforming Methods](#transforming-methods)
        1. [Other Things](#other-things)
    1. [Iterables](#iterables)
    1. [Map, Set, WeakMap, WeakSet](#map,-set,-weakmap,-weakset)
        1. [Map](#map)
        1. [Set](#set)
        1. [WeakMap, WeakSet](#weakmap,-weakset)
    1. [Object.keys ,values, entries](#object.keys-,values,-entries)
    1. [Destructuring Assignment](#destructuring-assignment)
    1. [Date and Time](#date-and-time)
    1. [JSON](#json)
1. [Advanced Working with Functions](#advanced-working-with-functions)
    1. [Rest Parameter and Spread Operator](#rest-parameter-and-spread-operator)
    1. [Closures](#closures)
    1. [Global Objects](#global-objects)
    1. [Function object, NFE](#function-object,-nfe)
    1. [new Function](#new-function)
    1. [Scheduling](#scheduling)
    1. [Decorators and forwarding, call/apply](#decorators-and-forwarding,-call/apply)
    1. [Function Binding, Currying and Partials](#function-binding,-currying-and-partials)
1. [Object Properties Configuration](#object-properties-configuration)
    1. [Property Flags and Descriptors](#property-flags-and-descriptors)
    1. [Sealing an Object Globally](#sealing-an-object-globally)
    1. [Property Getters, Setters](#property-getters,-setters)
1. [Prototypes, Inheritance](#prototypes,-inheritance)
    1. [Prototypal Inheritance](#prototypal-inheritance)
    1. [F.prototype](#f.prototype)
    1. [SKIPPED Prototype methods, objects without __proto__](#skipped-prototype-methods,-objects-without-__proto__)
    1. [SKIPPED Getting all properties](#skipped-getting-all-properties)
1. [Classes](#classes)
    1. [Class Inheritance](#class-inheritance)
1. [Error Handling](#error-handling)
    1. [Try...Catch](#try...catch)
    1. [Custom Errors, Extending Error](#custom-errors,-extending-error)
1. [Promises, Async, Await](#promises,-async,-await)
    1. [Promise](#promise)
    1. [Promise Chaining](#promise-chaining)
    1. [Error Handling](#error-handling)
    1. [Promise API](#promise-api)
    1. [Promisification](#promisification)
    1. [Microtasks](#microtasks)
    1. [Async/Await](#async/await)

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
    - If `return` is called with a primitive, the primitive is ignored and `this` object is returned



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

### Strings
- Single quotes, double quotes, backticks
- Escape characters, also `\u00A9, \u{1F60D} for unicodes`
#### Basic Accessing
- `"abc".length == 3`
- `mystr[3], mystr.charAt(3)`
    - For `[..]` if out of range, will get undefined
    - For `.charAt(..)` if out of range, will get empty string
- `for (let char of mystr) { ... }`
- `.toLowerCase()` `.toUpperCase()`
#### Finding, Testing, Slicing
- `.indexOf(substr [, startingPos])`, will return -1 if not found. Also `.lastIndexOf(...)`
    - TRICK: Use bitwise or to test if a value is -1 or not: `~mystr.indexOf("test") <--> "if found"`
- `includes` `startsWith` `endsWith`
- `.slice(start [, end])` `.substring(start [, end])` `.substr(start [, length])`
#### Unicode Encoding
- `.codePointAt(pos)` returns the unicode number of the character at position pos in the string
- `String.fromCodePoint(code)` returns the character by providing unicode number
- To "clean up" unicode characters, use `.normalize()`

### Arrays
- Syntax is like Python, also do not care about type
- Also works with `let a = new Array(...)`, do not use
- Use `.length` to get length
- Supports `shift` `unshift` `push` `pop`, supports adding multiple items at a time
- It is a kind of object
- When printed, it is comma separated values
#### Adding, Accessing, Finding Methods
- `.splice(index [deleteCount [elementToAdd ... ]]) -> itemRemovedAsArray`
- `.slice(start [end])`
- `arr.concat(arr1, arr2, ...)` Adds the arguments to the end of the `arr`
    - If `Symbol.isConcatSpreadable` is set for the argument, it will be spreaded, otherwise, will add as a whole
- `.indexOf` `.lastIndexOf` `.includes`
- `.find(function (item, index, array) { .. })`, also `.findIndex(.. same thing ..)`
    - item is the current item; index is current index; array is the whole array
    - the function is applied to each element until there is one that is true, if so the item is returned; if not found, `undefined` will be returned
    ```js
        let users = [
      {id: 1, name: "John"},
      {id: 2, name: "Pete"},
      {id: 3, name: "Mary"}
    ];

    let user = users.find(item => item.id == 1);
    ```
- `.filter( (item, index, array) => boolean )` returns a list
#### Transforming Methods
- `.map( (item, index, array) => newItem )` Applies a function to each element
- `.sort( customizedSortingFunction -OR- default: StringComparsion )`
    - The sorting function should return positive value if the first argument is bigger
- `.reduce( (prevValue, item, index, array) => Number, initialValue)` also `.reduceRight(...)`
- `.reverse()`
- `string.split(byWhatString)` `arrOfString.join(useWhatStringAsGlue)`
#### Other Things
- `Array.isArray(object)` tests if an object is an array or not
- Can provide `thisArg` to most array functions to provide `this` context

### Iterables
- When a `for..of` is call on an object
    - the object needs to implement `Symbol.iterator`
    - Such method will return a iterator which will be hold on to
    - this iterator should have a `next` function which returns a `{ done: Boolean, value: any }`
> NOTE: Array-like vs Iterable
> Array-like: when an object has numbers as keys and has length property
> Iterable: when an object has `Symbol.iterator` implemented
- `Array.from(object [mapFunction [this]])` Creates array from iterator or array-like object

### Map, Set, WeakMap, WeakSet
#### Map
- Like a object where it stores key-value pairs
- Map can use objects as keys!!
- Map use `===` to compare objects (at least think of it this way)
- Use `new Map()` `.set(key, value)` `.get(key)` `.has(key)` `.delete(key)` `clear()` `.size()`
- `for..of`: `map.keys()` `map.values()` `map.entries()` (default) same as simply `map`
- it has its own `forEach( Fn )`

#### Set
- `new Set([iterable such as array])`
- `.add(value)` `.delete(value)` `.has(value)` `.clear()` `.size`
- Provides `for..of` `.forEach`
- Provides `.keys()` `.values()` `.entries()`

#### WeakMap, WeakSet
- For Set, the values will not be hold on to, garbage collection will take place when needed
- For Map, it is similar, but only it applies to the keys, and the keys can only be objects
- For Map, it only has these methods for technical problems: `.get(key)` `.set(key, value)` `.delete(key)` `.has(key)`

### Object.keys ,values, entries
- Implement `.keys() .values() .entries()` for map-like data structures
- These methods for object looks different: use `Object.keys(obj)` instead. Real array will be returned (in stead of iterables)

### Destructuring Assignment
- Array
    ```js
    let [a, b, c] = "abc";  // with iterables
    let [a, , c] = [A, B, C]  // skipping elements
    let [name1, name2, ...rest] = [A, B, C, D, E, F] // get the rest as array
    let [a = "A", b = "B"] = [A]  // default values

- Object
    ```js
    let {var1, var2} = {var1: ..., var2: ...}
    // "Extracting out some properties of the object using its name"

    let {width: w, height: h, title} = options;
    // "what: goesWhere"

    let {width: w = prompt("width?") } = options;  // Default values

    // [!] When used without let keyword, put whole statement inside parentheses
    ({width: w, height: h, title} = options);
    ```

- Nested
- For function parameters
    ```js
    function showMenu({
        title = "Untitled",
        width: w = 100,  // width goes to w
        height: h = 200, // height goes to h
        items: [item1, item2] // items first element goes to item1, second to item2
        }) {
        alert( `${title} ${w} ${h}` ); // My Menu 100 200
        alert( item1 ); // Item1
        alert( item2 ); // Item2
    }

    // General Form
    function({
        incomingProperty: parameterName = defaultValue
    } [ = {}]) {
        ...
    }
    ```

### Date and Time
- `new Date([milliseconds] = now)` after the Jan 1 1070 +0000
- `new Date("YYYY-MM-DD")` or use `Date.parse(str)` in the form of `YYYY-MM-DDTHH:mm:ss.sssZ, T is delimiter, Z as UTC+0, can be replaced with +-hh:mm`
- `new Date(YYYY, M, D, H, M, S, MS)`
- `.getFullYear()` `.getMonth()` `.getDate()` `,getHours/Minutes/Seconds/Milliseconds()`
- `setFullYear(year [, month, date])`
- `setMonth(month [, date])`
- `setDate(date)`
- `setHours(hour [, min, sec, ms])`
- `setMinutes(min [, sec, ms])`
- `setSeconds(sec [, ms])`
- `setMilliseconds(ms)`
- `setTime(milliseconds)` (sets the whole date by milliseconds since 01.01.1970 UTC)
- It auto corrects inputs
- When converted to numbers, is equivalent to `.getTime()`, yields milliseconds
- When subtracted, yields difference in ms
- `Date.now()` <-> `new Date().getTime()`

### JSON
- functions, symbolic properties, undefined are ignored
- `JSON.stringify(obj [, replacer, space])`
    - `replacer`: pass an array of strings representing key names; nested objects keys also count
    - Or, `replacer`: a function `(key, value) => replacedValue`; it will also receive the object itself at the beginning, with `""` as key
    - `space`: number of spaces for the output indent
- Can implement `.toJSON() -> str` to customizes json output
- `JSON.parse(str [, reviver])`
    - `reviver`: takes a function `(key, value) -> transformedValue`


## Advanced Working with Functions

### Rest Parameter and Spread Operator
- Use `...array` to spread them
- Use `function max(a, b, ...rest)` to get rest parameters
- Can also use `arguments` inside a function (excluding arrow function) to get arguments, it is array-like, iterable, but not array


### Closures
- Each function will have a hidden property containing its lexical environment, which has a reference to the outer environment
- When a function is called, it will search for variables from its own environment first and layer by layer out

### Global Objects
- use `type="module"` in script tag to isolate the script from the global window object

### Function object, NFE
- `func.name` will return the function's name
- `func.length` will return the number of parameters of the functions, without rest parameter
- "polymorphism" when do different things according to the arguments
- Can add properties to functions
- Give the function expression a name (Named Function Expression), so that the function can reference itself internally, in case the variable got reassigned

### new Function
- `new Function( ... argument names ..., function body)` all of the arguments are string
- Can also be `new Function('a,b,c', return a+b+c')`
- Functions created this way will capture the global one as its lexical environment

### Scheduling
- `let timerId = setTimeout(func/code, [delay in ms], [arg1], [arg2], ...)`
- `clearTimeout(timerId)`
- Same but run by schedule: `setInterval(...)` `clearInterval(...)`
- Use `setTimeout(codeToRun, 0)` or simply `setTimeout(codeToRun)` to run something asynchronously

### Decorators and forwarding, call/apply
- Can write a function that creates a cached version of any functions
- When used for functions of functions, need to provide `this` context, use `funcName.apply(context, argsAsArray)`
- Use `func.apply()` for argument arrays; use `func.call()` for iterable or array arguments with spread operator
- When `arguments.join()` does not work, use `[].join.call(arguments)`

### Function Binding, Currying and Partials
- `let sayHi = user.sayHi.bind(user);` gets a callable thing which, when being called, will call the original function with correct this context
- Can also fixes some arguments for a function
    ```js
    function mul(a, b) { return a * b; }
    let double = mul.bind(null, 2);
    ```
- **Currying**: Transform a function `f(a, b, c)` into callable as `f(a)(b)(c)`


## Object Properties Configuration

### Property Flags and Descriptors
- Each property has flags, `writable` `enumerable` `configurable`
- Use `Object.getOwnPropertyDescriptor(obj, propertyName)` to get; will get a descriptor object
- use `Object.defineProperty(obj, propertyName, descriptor)` to set new property or change property descriptor. When creating new property, use `value: ...` to set the value, property configurations not listed are default to be false
- `writable` when false, the value is read only
- `enumerable` when false, the key will not appear in `for..in` or `Object.keys(obj)`
- `configurable` when false, the object property cannot be configured, this is a one-way operation
- `Object.defineProperties(obj, descriptors)`, where `descriptors` is a object with key as name, value as descriptor.
- `Object.getOwnPropertyDescriptors(obj)` might be useful sometimes

### Sealing an Object Globally
- `Object.preventExtensions(obj)` forbids addition of new properties
- `Object.seal(obj)` sets `configurable: false` for all existing proeprties
- `Object.freeze(obj)`
- Tests for above: `Object.isExtensible() .isSealed() .isFrozen()`

### Property Getters, Setters
    ```js
    let obj = {
        get fullName() { ... },
        set fullName(value) { ... }
    }
    ```
- Properties that are created like these are called *accessor properties*; other normal properties are called *data properties*.


## Prototypes, Inheritance

### Prototypal Inheritance
- `[[Prototype]]`
- Set `obj.__proto__` to another object to inherits from another object
- Each object can only have one prototype
- `this` context will be the object before dot

### F.prototype
- Can set `.prototype` for object constructor functions: when new object is created ie `new F()`, the resulting object will have `__proto__ = ` the parent object
- We can borrow some methods from other object by setting

### SKIPPED Prototype methods, objects without __proto__
### SKIPPED Getting all properties

## Classes

```js
class User {
    var isAdmin = false;
    constructor(name) { this.name = name };
    sayHi() { console.log(this.name); }
}

class SuperUser extends User {
    constructor(name, level) { super(name); this.level = level; }
    saySuper() { console.log("super"); }
    sayHi() { super.sayHi(); console.log("and super"); }
}
```

### Class Inheritance
- `[[HomeObject]]` comes to rescue when calling `super`

- Static Methods are those that belong to the class, not any particular objects
    ```js
    class User {
        static compareUser(a, b) { return a.id - b.id; }
        ...
    }

    // Equivalent to
    // ... (other declarations here)
    User.compareUser = function(a, b) { return a.id - b.id; };
    ```

## Error Handling
### Try...Catch
```js
try {

} catch (err) {
    if (err.name = 'SyntaxError') {
        console.log(err.message);
        err.stack = "<nested calls>"; // Non-standard, but is supported by most env
        // ...
    } else if (err instanceof TypeError) { // Can also use this
        throw err;
    }

} finally {
    // ...
}
```

### Custom Errors, Extending Error
```js
// The "pseudocode" for the built-in Error class defined by JavaScript itself
class Error {
  constructor(message) {
    this.message = message;
    this.name = "Error"; // (different names for different built-in error classes)
    this.stack = "<nested calls>"; // non-standard, but most environments support it
  }
}

// To extend:
class ValidationError extends Error {
    constructor(message) {
        super(message);
        this.name = this.constructor.name;
    }
}
```

## Promises, Async, Await
### Promise
```js
let promise = new Promise(function(resolve, reject) {
    // do something here
});
```

- The promise takes in one function, which:
    - has two arguments, returns nothing. The two arguments:
    - first one, usually called resolve, second one, usually called reject
- We should call appropriate function when we are done
    - We should only call function once, any further call will be ignored

- `promise.then(handleSuccess, handleError)`, when only interested in success, provide just first argument
- `promise.catch()` handles error
- `promise.finally()` runs when the promise is settled

### Promise Chaining
- Can have a return statement in handler, the return value will become the result of the promise returned
- Or, can return a Promise in the handler. Any further `.then` will not be executed until the new promise is resolved
- `Thenable` object

### Error Handling
- The promise executor is implicitly wrapped in try-catch block
- `throw new Error()` is equivalent to `reject(new Error())`
- When there is an unhandled rejection,  the engine will generate a global error `unhandledrejection`
- In brower environment, we can use `window.addEventListener('unhandledrejection', function(event) { ... }`

### Promise API
- `Promise.resolve(value)` <--> `new Promise((resolve, reject) => resolve(value))`
- `Promise.reject(error)` <--> `new Promise((resolve, reject) => reject(error))`
- `Promise.all([...promises...])` returns a list of resolved values, in the order they appear in the array, or rejects immediately with the error and ignores other promises
- `Promise.allSettled(promises)` (recently added)
- `Promise.race(promises)`

### Promisification
- It means the conversion of a function that accepts a callback into a function that returns a promise
- Note: use promisify only when want to use async/await. Callback can be technically called many times but a promise can be only resolved once
- In nodeJS, there is util.

### Microtasks
- The engine will takes all tasks, put them in a first-in-first-out queue, execute them only when the script is idle

### Async/Await
- adding keyword `async` before a function will ensure that the function returns a promise, and wrap any other values in a `Promise.resolved()`
- Use `let result = await promise;` to make the program pause, until the promise is resolved.
- Note: `await` only works *inside* `async` functions
- When desired, can wrap code inside an anonymous async function, like this
    ```js
    (async () => {
    let response = await fetch('/article/promise-chaining/user.json');
    let user = await response.json();
    ...
    })();
    ```
- When the function being `await`-ed is not resolved, throws an error, use `try...catch` to catch the error



