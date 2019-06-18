# Java Notes

> 2019-06-15
> https://youtu.be/n-xAqcBCws4


- `java.util.*`
- `final` for constants

- Data Types
    - byte
    - short
    - char (single quotes)
    - int
    - float (end with upper F)
    - double (end without a F)
    - long (can use underscore to help read) (ends with L)

- To convert
    - To smaller type `(<type>) oldVar`
    - To string `Double.toString(oldVar)`

- String is object (reference type)

- String
    - `.charAt(1)` `.contains("str")` `.length()`
    - `.equals(other)` `.equalsIgnoreCase(other)`
    - `.compareTo(other)`
    - `.replace("from", "to")`
    - `.substring(from, stops)`
    - `.split(sep)`
    - `.trim()` `.toUpperCase()` `.toLowerCase()`

- String Builder
    - `StringBuilder a = new StringBuilder("some string");`
    - `.length()` `.capacity()` `.insert(index, "new")`
    - `.replace(fromIndex, toIndex, "with")` `.delete(fromIndex, toIndex)`
    - `.indexOf("some string")`

- String Buffer is used when using Threads

- Array
    - `int[] a = new int[10];`
    - `Arrays.fill(a, 2);`
    - `a.length`
    - `String[] b = { "abc", "cde" };`
    - `Arrays.binarySearch(a, toSearch);`

    - `int m[][] = new int[row][col];`

    - `Arrays.copyOf(fromArray, howMuch)`
    - `Arrays.equals(a, b)`
    - `Arrays.sort(a)`
    - `Arrays.toString(a)`
    - `Arrays.asList(1,2,3,4)`

- ArrayList
    - `ArrayList<String> a1 = new ArrayList<String>(20);`
    - `a1.add("Abc");`
    - `a1.get(where)`
    - `a1.set(where, toWhat)`
    - `a1.remove(where)`
    - `a1.clear()`

- Iterator
    - `Iterator it = a1.iterator()`
    - `it.hasNext()` `it.next()`

- Linked List
    - `LinkedList<Integer> a = new LinkedList<Integer>();`
    - `.add(1)` `.addAll(Arrays.asList(1,2,3))` `.addFirst(1)` `.addLast(2)`
    - `.contains(4)` `.indexOf(4)` `.set(where, what)` `.get(where)` `.getFirst/Last()`
    - `.clear()` `.size()`

- Scanner
    - `Scaner sc = new Scanner(System.in);`
    - `sc.hasNextLine()` `.nextLine()` `.nextInteger/Short()`

- `switch(var) { case "a": case "b": some(); break; default: someOther(); }`

- `for` `while` `do {} while`


```
            │ Class │ Package │ Subclass │ Subclass │ World
            │       │         │(same pkg)│(diff pkg)│
────────────┼───────┼─────────┼──────────┼──────────┼────────
public      │   +   │    +    │    +     │     +    │   +
────────────┼───────┼─────────┼──────────┼──────────┼────────
protected   │   +   │    +    │    +     │     +    │
────────────┼───────┼─────────┼──────────┼──────────┼────────
no modifier │   +   │    +    │    +     │          │
────────────┼───────┼─────────┼──────────┼──────────┼────────
private     │   +   │         │          │          │

 + : accessible         blank : not accessible
```

- `<public | private | protected> [static] <returnType | void> <funcName>(<argType> <argName>, ..)`
- `... getSum(int ... nums) { } // nums is an array`

- Enhanced For Loop
    - `for (int x: a) { balabala(); }`

- `List<Object>` can contain different types

- enum
    - `enum Day { Monday, Tuesday, Wednesday };`
    - `Day somevar = Day.Monday;`

- Exceptions
    - `try { ... } catch (Exception e) { ...; e.getMessage(); e.toString(); } finally { ... }`
    - `throw new Exception("Error msg")`

- Interface
    - `class <someClass> implements <someInterface> { ... }`

> Stopped at 1:35:00

- Collectors, Stream

