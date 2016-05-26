# Python Notes
Notes in flux: interesting tricks and tipps worth knowing/learning.

### Useful Packages

- [tqdm](https://pypi.python.org/pypi/tqdm) - A Fast, Extensible Progress Meter
```python
    from tqdm import tqdm
        for i in tqdm(range(9)):
    ...
```


### pdb Debugger
Command      | Description
-------------|---------------------------------------------------------
`h pdb`      | help on pdb
`w(here)`    | print stack trace. An arrow indicates the current frame
`u(p)`       | move current frame one level _up_ (to an older frame)
`d(own)`     | move current frame one level _down_ (to a newer frame)
`b(reak)`    | list all breakpoints
`b [filename:]lineno` | set breakpoint at line-number in file (or current file)
`b function` | set breakpoint at first line in the function
`cl(ear)`    | clear all breakpoints (or selected numbers if given)
`tbreak`     | temporary break
`s(tep)`     | execute current line; stop at the first possible occasion
`n(ext)`     | continue execution until the next line in the current function is reached or it returns
`r(eturn)`   | continue execution until the current function returns
`c(ontinue)` | continue execution
`l(ist) [first] [,last]]` | list source code (11 lines if first/last not given)
`a(args)`    | print the argument list of the current function
`p expr`     | print the value of the expression `expr`
`! statement` | execute one-line statement (useful if statement overlaps with a pdb command)
`whatis arg`  | prints the type of the argument `args`
`alias [name [command]]` | creates an alias
`q(uit)`      | quit pdb