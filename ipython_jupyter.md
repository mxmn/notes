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
-



### Jupyter Customization
- add line numbers and line wrapping. Add this code snippet to
  `~/.jupyter/custom.custom.js`:

```python
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
