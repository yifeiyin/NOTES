## Renaming Files
- substitute plus sign with space
- run this command directly in bash
`for file in *.pdf; do mv "$file" "$(echo $file | sed 's/+/ /g')"; done`



## Vim Syntax Highlighting
> [ref](https://stackoverflow.com/a/43302456/7318257)
Use #! at the beginning to indicate the file type.
