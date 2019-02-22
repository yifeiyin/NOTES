Shell Notes
===========

Yifei Yin,  January 9 2019 at Toronto

Meta Info
---------

Borune Shell: [wikipedia](https://en.wikipedia.org/wiki/Bourne_shell)
Possible good book: [Bourne Shell Scripting Tutorial](https://www.shellscript.sh/functions.html)


Things To Look Into
-------------------
- `sed`
- `grep`
- `cut`: text slicing


Single, Double Quotes
---------------------
- [StackOverflow](https://stackoverflow.com/questions/6697753/difference-between-single-and-double-quotes-in-bash)
- Single quotes: does not interpolate anything, even \' will not work.
- Double quotes: can use backslash to escape special characters, variables are evaluated.
- [Useful Table](https://stackoverflow.com/a/42082956/7318257)
- Sometimes need to use ANSI-C Quoting


Variables
---------
- By convention, use all uppercase names
- `NAME="something"`    (No spaces around)
- `unset NAME`
- `readonly NAME`
- `echo $NAME`


Functions
---------
- To define:
    ```
    function my_function {
        command1
        command2
    }
    # -- OR --
    my_function() {
        command1
        command2
    }
    ```
- Use $1, $2, $3, ... to access corresponding parameters. $@ for all parameters.

