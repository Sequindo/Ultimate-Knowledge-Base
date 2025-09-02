# Bash useful hotkeys

Not all are mentioned, only these useful ones (for me), omitting ones that I know.

## Moving

| cmd  | desc                    |
|----------|--------------------------------|
| ctrl + a | Goto BEGINNING of command line |
| ctrl + e | Goto END of command line       |
| ctrl + b | move back one character        |
| ctrl + f | move forward one character     |
| alt + f  | move cursor FORWARD one word   |
| alt + b  | move cursor BACK one word      |
| ctrl + xx | Toggle between the start of line and current cursor position |

## Edit / Other

| command  | description                    |
|----------|--------------------------------|
| ctrl + d          | Delete the character under the cursor |
| ctrl + h          | Delete the previous character before cursor |
| ctrl + u          | Clear all / cut BEFORE cursor |
| ctrl + k          | Clear all / cut AFTER cursor |
| ctrl + w          | delete the word BEFORE the cursor |
| alt + d           | delete the word FROM the cursor |
| ctrl + y          | paste (if you used a previous command to delete) |
| ctrl + i          | command completion like Tab
| ctrl + l          | Clear the screen (same as clear command) |
| ctrl + c          | kill whatever is running |
| ctrl + d          | Exit shell (same as exit command when cursor line is empty) |
| ctrl + z          | Place current process in background |
| ctrl + _          | Undo |
| ctrl + x ctrl + u	| Undo the last changes. ctrl+ _ does the same |
| ctrl + t          | Swap the last two characters before the cursor |
| esc + t           | Swap last two words before the cursor |
| alt + t           | swap current word with previous |
| alt + [Backspace] | delete PREVIOUS word |
| alt + <           | Move to the first line in the history |
| alt + >           | Move to the end of the input history, i.e., the line currently being entered |
| alt + ?           | display the file/folder names in the current path as help |
| alt + *           | print all the file/folder names in the current path as parameter |
| alt + .           | print the LAST ARGUMENT (ie "vim file1.txt file2.txt" will yield "file2.txt") |
| alt + c           | capitalize the first character to end of word starting at cursor (whole word if cursor is at the beginning of word)|
| alt + u           | make uppercase from cursor to end of word |
| alt + l           | make lowercase from cursor to end of word |
| alt + p           | Non-incremental reverse search of history. |
| alt + r           |Undo all changes to the line|
| [TAB]             | Auto complete |
| cd -              | change to PREVIOUS working directory |
