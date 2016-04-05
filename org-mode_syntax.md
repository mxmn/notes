## org-mode Compact Formatting Syntax Cheatsheet

For more detailed information, see the for instance the
[Markup for rich export](http://orgmode.org/manual/Markup.html)
section of the org-mode manual.


#### Emphasis

Use `*bold*`, `/italic/`, `_underlined_`, `=verbatim=` and `~code~`, and, if you
must, `‘+strike-through+’`.

Formatting | Example
----------- | --------
`*bold*` | **bold**
`/italic/` | *italic*
`_underlined_` | underlined
`=verbatim=` | `verbatim`
`~code~` | `code`
`‘+strike-through+’` | ~~strike-through~~



#### Literal examples
- Extended example:

    ```
    #+BEGIN_EXAMPLE
    Some example from a text file.
    #+END_EXAMPLE
    ```

- Small example (colon ":" followed by a whitespace):

  Here is an example
     `: Some example from a text file.`

- Language specific source code:

    ```
    #+BEGIN_SRC emacs-lisp
      (defun org-xor (a b)
         "Exclusive or."
         (if a (not b) b))
    #+END_SRC
    ```
