JavaScript Notes
================

> 2019 March 10
> Reading javascript.info

## JavaScript Fundamentals

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

    
