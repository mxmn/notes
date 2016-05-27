## Compact Markdown Cheatsheet

For more detailed information, see the
[original specs](http://daringfireball.net/projects/markdown/), or the
[markdown-here
wiki](https://github.com/adam-p/markdown-here/wiki). GitHub usage of
markdown is described
[here](https://help.github.com/categories/writing-on-github/).

#### Headings


From `#` to `######` (H1 to H6).
Two alternatives for H1 and H2 are:

    Header 1
    ========
    Header 2
    --------


#### Emphasis

Formatting           | Example
---------------------|------------------------------------
`**bold**, __bold__` | **bold**, __bold__
`*emph*, _emph_`     | *emph*, _emph_
`~~strikethrough~~`  | ~~strikethrough~~
'monospace'  (with _backtick_; _grave accent_) | `monospace`


#### Highlighting

Inline `monospace syntax` highlighting uses single back-ticks.

Blocks of code use three back-ticks, or are indented with 4 spaces. A language specification might be supported, as for example for python:


    ```python
    def function(a, b=0):
        if a == b:
            return c
    ```

```python
def function(a, b, c=0):
    if a == b:
        return c
```

Blockquote paragraphs start with "> ", as e.g. in `> Testing a blockquote.`

> Testing a blockquote.

#### Misc

Ordered and unordered lists are created with numbers, and `*, -, +`,
respectively. The indentation allows a hierarchical structure.

Links are built in the form of `[visible description](link)`. One can
link to websites, files, and reference labels.  Reference labels are
defines separately in the form of `[ref-name]: link`.


Horizontal rules are built with at least three `***`, or `---`, or `___`:

***
_________________________________________________
