# IPython and Jupyter Notes
Note of caution: some configuration options might have changed (current stand: May 2016).


### IPython Startup / Init
- execute python scripts with `ipython -i --pdb` in order to continue
  in the interactive mode by the end of the script or to start the
  debugger in case of uncaught exceptions.
- setup coe to always be run on start-up. Add the lines to the file in
  the `myprofile` directory: `$myprofile/startup/00-always-import.py`:

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
```


### Useful Magic commands
- `%debug` will switch to `ipdb` if called right after an error. Alternatively, it allows to setup breakpoints before executing a command.
- `%pdb` will enable automatic switch to `ipdb` in case an error occurs in the program.

### Jupyter Snippets

#### Standard Configuration
```python
from __future__ import absolute_import, division, print_function

import os, sys
import json

%pylab inline
plt.rcParams['figure.figsize'] = (10.0, 8.0) # set default size of plots
#plt.rcParams['image.interpolation'] = 'nearest'
#plt.rcParams['image.cmap'] = 'gray'

# for auto-reloading external modules
# see http://stackoverflow.com/questions/1907993/autoreload-of-modules-in-ipython
%load_ext autoreload
%autoreload 2
```

### Jupyter Customization
- add line numbers and line wrapping. Add this code snippet to
  `~/.jupyter/custom.custom.js`:

```javascript
define([
    'base/js/namespace',
    'base/js/events'],
    function (IPython, events) {
        events.on("app_initialized.NotebookApp",
            function () {
                IPython.Cell.options_default.cm_config.lineNumbers = true;
                IPython.Cell.options_default.cm_config.lineWrapping = true;
            }
        );
    }
);
```
