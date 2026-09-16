# Cryptonite Technical Recruitment 2026-27
## Linux Luminarium
1) [Hello Hackers](Linux%20Luminarium/1-hello-hackers.md)
2) [Pondering Paths](Linux%20Luminarium/2-pondering-paths.md)
3) [Comprehending Commands](Linux%20Luminarium/3-comprehending-commands.md)
4) [File Globbing](Linux%20Luminarium/3-file-globbing.md)
5) [Practicing Piping](Linux%20Luminarium/5-practicing-piping.md)
6) [Processes and Jobs](Linux%20Luminarium/6-processes-and-jobs.md)
7) [Perceiving Permissions](Linux%20Luminarium/8-perceiving-permissions.md)
8) [Chaining Commands](Linux%20Luminarium/8-chaining-commands.md)
9) [Pondering PATH](Linux%20Luminarium/6-pondering-path.md)

## PY4E
1. [Variables, expressions, and statements](py4e/1-variable-expressions-statements.md)
2. [Conditional execution](py4e/2-conditional-execution.md)
3. [Functions](py4e/3-functions.md)
4. [Loops and iterations](py4e/4-loops-iterations.md)
5. [Strings](py4e/5-strings.md)
6. [Files](py4e/6-files.md)
7. [Lists](./py4e/7-lists.md)
8. [Dictionaries](./py4e/8-dictionaries.md)
9. [Tuples](./py4e/9-tuples.md)
10. [Regular Expressions](./py4e/10-regex.md)

## Points to Remember
### Piping commands
- `>` redirects the command output while `<` redirects input into command
- `>` by default assumes `1>`
- File descriptors are communication channels in linux
- 0 means standard input.
- 1 means standard output.
- 2 means standard error.
- It is used as `2>` as we are redirecting the output
- `>&` is used to redirect a file descriptor to another file descriptor. We can therefore use this as `2>& 1` which means we are redirecting the standard error to standard output.

### Commands
- `grep -v` inverts the grep search
- `tee` (named after t-splitter in plumbing) allows us to duplicate data flowing through pipes.

### Python
- strip() to remove trailing whitespaces(spaces, tab, newlines) from both ends
- rstrip() to remove trailing whitespaces from right end
