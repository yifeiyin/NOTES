Use Package Control

> **WARNING: Archived Notes**
>
> These notes are no longer being maintained and are here for archive purpose only. Some usage may be deprecated in current standard.

### Install: 

* Sublime REPL 
* SublimeCodeIntel (for code completion)
* MagicPython (for better python highlighting)

### Under Sublime Key Bindings, add:
```
// ////// command r -> Run python file
    {
        "keys": ["super+r"],
        "caption": "SublimeREPL: Python - RUN current file",
        "command": "run_existing_window_command",
        "args": {
            "id": "repl_python_run",
            "file": "config/Python/Main.sublime-menu"
        },
                "context": [
        { "key": "selector", "operator": "equal", "operand": "source.python" }]
    },
 // ////// command b -> Run python file
    {
        "keys": ["super+b"],
        "caption": "SublimeREPL: Python - RUN current file",
        "command": "run_existing_window_command",
        "args": {
            "id": "repl_python_run",
            "file": "config/Python/Main.sublime-menu" 
        },
        "context": [{ "key": "selector", "operator": "equal", "operand": "source.python" }]
    },
 // ////// ctrl c -> send SIGINT, aka KeyboardInterrupt
    {
        "keys": ["ctrl+c"], 
        "command": "subprocess_repl_send_signal", 
        "args": {"signal": 2},
        "context": [{ "key": "setting.repl", "operator": "equal", "operand": true }]
    },
```

### Under SublimeREPL Settings, add:
```
// standard sublime view settings that will be overwritten on each repl view
// this has to be customized as a whole dictionary

// ///////// For syntax highlighting
{
    "repl_view_settings": {
        "syntax": "Packages/Text/Plain text.tmLanguage"
    },
}
```

## Other cool packages

* ayu, command palette is super cool, but I don't like other stuff very much
* a file icon, very cool!
* colorsublime, preview color themes
