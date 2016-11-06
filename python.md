# Python Notes
Notes in flux: interesting tricks and tips worth knowing/learning.

### Python / IPython Code Snippets
- simple logging setup
```python
import logging
logging.basicConfig(filename=log_file, level=logging.INFO,
                    format='%(asctime)s %(name)-12s %(levelname)-8s %(message)s')
logging.info("info message")
```
- text progress bar
```python
from tqdm import tqdm
for i in tqdm(range(9)):
    ...
```

- command line arguments are available in the list `sys.argv` with `sys.argv[0]` being the name of called script
```python
print sys.argv
```

- file processing via streams/pipes, for instance to apply additional command line operations on the file, as e.g. unzip:
```python
from subprocess import Popen, PIPE
process = Popen(['zcat', '-f', gz_file], stdout=PIPE, stderr=PIPE)
stdout, stderr = process
for line in stdout:
    pass
```
or
```python
from subprocess import Popen, PIPE
input_stream = Popen(['zcat', '-f', gz_file], stdout=PIPE)
for line in input_stream.stdout:
    pass
```

- Note: `shell=True` is considered a security risk when used to process untrusted data. A clever attacker can modify the input to access arbitrary system commands. E.g. by inputting `filename.swf; rm -rf /` for the value of filename.


### Useful Packages

- [tqdm](https://pypi.python.org/pypi/tqdm) - A Fast, Extensible Progress Meter
```python
    from tqdm import tqdm
    for i in tqdm(range(9)):
        ...
```

#### Numba
For example, use `jit` decorator to speed up loop functions (e.g. by a factor of 200):

```python
from numba import jit
@jit
def jit_simulate():
    while True:
        ...
```

#### Speed & Memory
- Lookups in lists are *O(n)*, in dicts they are amortized *O(1)* (in
  dependence of the number of elements in the dict).
  * use dicts for lookup if number of elements is *reasonable*.
  * an alternative is to use a sorted list and then to use a binary
    search, which will be *O(log(n))*. (The sorting will be *O(n
    log(n))*.). One could use the *bisect* module for this:
```python
    from bisect import bisect_left
    def bi_contains(lst, item):
        """ efficient `item in lst` for sorted lists """
        # if item is larger than the last its not in the list, but the bisect would
        # find `len(lst)` as the index to insert, so check that first. Else, if the
        # item is in the list then it has to be at index bisect_left(lst, item)
        return (item <= lst[-1]) and (lst[bisect_left(lst, item)] == item)
```
- Dicts and sets use hashing and therfore much more memory than needed
  for the element objects only.

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


### Python 2 and 3 Compatibility

First, add the future import to Py2 files:
```python
from __future__ import absolute_import, division, print_function
```
optionally, one could add the `unicode_laterals` as well, but this is not advisable in the general sense (see [link](http://python-future.org/unicode_literals.html#unicode-literals)).


Explicit imports of Py3 builtins into Py2:
```python
from builtins import (ascii, bytes, chr, dict, filter, hex, input,
                      int, map, next, oct, open, pow, range, round,
                      str, super, zip)
```
