GDB Debugger, Mar 19 2019

To start: `gdb executableFile`

- `q, quit`
- `r, run`
- `n, next`: run next line
- `c, continue`: run without breakpoints(?)

- print
    - `p, print`
    - `p varName`
    - `p varName = newValue` assigns new values

- breakpoint
    - `b, break`
    - `b functionName`
    - `b fileName:[lineNumber]`
    - `b [lineNumber]`

- Misc
    - `l, list [number]`: show code
    - `info locals`: show all local vars
    - `info breakpoints`: show all breakpoints
    - `<enter>`: repeat last command
    - `make fileName`
    - `disable`: disables breakpoints
