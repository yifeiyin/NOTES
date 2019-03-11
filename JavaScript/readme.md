JavaScript Notes
================

> 2019 March 10
> Reading javascript.info

## JavaScript Fundamentals

### Preliminaries
- `<script src='...'> </script>`
    - will load outside script and ingore content inside the tag

- Semicolons
    - Can be omitted in most cases for standalone statements
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
    - *Backticks* allow evaluation exists, use `${...}`: `alert( `1 + 1 = ${1 + 1}` );`
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

- Almost all math operations will convert values to numbers, *besides* `+`
    ```js
    1 + '2' // '12'
    '1' + 2 // '12'
    ```
- To Boolean: `Boolean(...)`
    - `'(empty string)', 0, null, undefined, NaN` are false
    - all others are true


