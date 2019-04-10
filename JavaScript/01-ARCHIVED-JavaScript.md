# JavaScript Notes

> **WARNING: Archived Notes**
>
> These notes are no longer being maintained and are here for archive purpose only. Some usage may be deprecated in current standard.

#### Where to find help

[Learn Web Development](https://developer.mozilla.org/en-US/docs/Learn)

[JavaScript Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)

[JavaScript Reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference)

----
> [Grammar and types](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar_and_types)

### Comments

- `/* ... */`
- `// ... `


### Declarations

- naming: starts with `$` `_` `letter`, contains `letter` `number` `_`.
- `var`: global variable which means it's function-scoped 
- `let`: local variable which means it's block-scoped 
- `const`block-scoped, read-only named constant, must have a initial value.
- JavaScript is case sensitive
- If no value is specified in the declaration, it is `undefined`.
- Use `a == undefined` to test whether a has a value.
- `undefined` is also evaluated to `false`
- `undefined + 2` is `NaN`
- `null` is 0


### Variable Hoisting

- `var` hoists the variable, `let` does not
- `var` Referring to a variable that is later been defined will get a `undefined`. 
- `let` Referring to a variable that is later been defined will get a `ReferenceError`. 


### Data Types

- Boolean: `true` `false`
- null: denotes a null value. It's different from `Null` `NULL`
- undefined: top-level property whose value is not defined.
- Number: integer or floating point number.
- String: text
- Symbol: A data type whose instances are unique and immutable.
- Object
- To convert string to number: use `parseInt()` or `parseFloat()` or use `+` sign: `+ '1.1' - 2`


### Literals

You use literals to represent values in JavaScript. These are fixed values, not variables, that you literally provide in your script.

#### Array literals
- For more, see `Array` objects
```
var coffees = ['French Roast', 'Colombian', 'Kona'];
```
```
var fish = ['Lion', , 'Angel'];
// fish[1] would be undefined
```
The extra comma in the end will be ignored, but only the last comma. In practice, explicitly say undefined.

#### Boolean Literals
- For more, see `Boolean` objects
`true` or `false`

#### Numeric Literals
- Decimal integer: without any leading zeros.
- Octal integers (base 8): Use `0` or `0o` or `0O` before.
- Hexadecimal integers (base 16): Use `Ox` `OX`. Use 0-9, a-f as values. They are not case sensitive.
- Binary integer (base 2): Use `0b` `0B` as prefix. Only 0 or 1.
- Float-point: `3.14159` `-.1234567` `-1.0e-20`

#### Object Literals
```
var car = {a: "suv", b: "200" }

car.a // = "suv", can also use car['a']
car.b // = 200, can also use car['b']
```
SKIPPED: Enhanced Object literals


#### RegExp Literals
```
var re = /ab+c/
```

#### String Literals
- For more, see `String` Objects
- Single quotes double quotes are both fine, just like python.
- String objects have method `.length`



##### Escaping Characters

- Use backslash to escape something, such as backslash itself, newline, quotes.

```
var str = 'this string \
is broken \
across multiple \
lines.' // str does not contain newline characters

var poem = 
'Roses are red,\n\
Violets are blue.\n\
Sugar is sweet,\n\
and so is foo.'
```

##### Template literals
```
// String interpolation
var name = 'Bob', time = 'today';
`Hello ${name}, how are you ${time}?`
```

> Optionally, a tag can be added to allow the string construction to be customized, avoiding injection attacks or constructing higher level data structures from string contents.

```
// Multi-line strings
var poem = 
`Roses are red, 
Violets are blue. 
Sugar is sweet, 
and so is foo.`
```

----

