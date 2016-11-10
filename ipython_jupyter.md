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

##### Standard Configuration
```python
from __future__ import absolute_import, division, print_function

import os, sys
# import json
# from collections import Counter, defaultdict
# import pandas as pd

from tqdm import tnrange, tqdm_notebook
# usage: for x in tqdm_notebook(some_iterable, "1th loop"):
#            for y in tqdm_notebook(another_iterable, "2nd loop"): do stuff
#    or: for i in tnrange(100): do stuf

# --no-import-all prevents importing * from numpy and matplotlib
%pylab inline --no-import-all

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

### Jupyter notebook extensions
The [nbextensions](https://github.com/ipython-contrib/jupyter_contrib_nbextensionsa)
can be installed following the guides on the
[site](https://github.com/ipython-contrib/jupyter_contrib_nbextensions):

```
conda install -c conda-forge jupyter_contrib_nbextensions
```

To activate a specific extension, one could either use the
nbextensions configurator (below), or one could pre-activate the
extensions prior to starting jupyter. E.g. to activate the table of
contents, use

```
jupyter nbextension enable toc2/main
jupyter-notebook
```

To explore and to enable/disable other extensions, use the
nbextensions configurator. With conda it can be installed via:

```
conda install -c conda-forge jupyter_nbextensions_configurator
```

Then (after restarting the notebook server), the configurator will be accessible under
`{base_url}/nbextensions`, as e.g.
[http://localhost:8889/nbextensions](http://localhost:8889/nbextensions)

- when time will be available, explore further extensions.
