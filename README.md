<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#orgheadline1">1. Introduction</a></li>
<li><a href="#orgheadline2">2. Requirements</a></li>
<li><a href="#orgheadline3">3. Usage</a></li>
<li><a href="#orgheadline4">4. Other tips and tricks</a></li>
</ul>
</div>
</div>

# Introduction<a id="orgheadline1"></a>

The epython package provides the `epython.org` file to help in setting
up some utilities for running python inside emacs. Org-babel files can
be turned into elisp files via something like

`(org-babel-tangle-file "epython.org" "epython.el" "emacs-lisp")`

(which yields `epython.el`) or loaded directly via something
like `(org-babel-load-file "epython.org")`. Org files can also be
exported to or markdown files (e.g., for github `README.md` files) via 

`M-x org-md-export-to-markdown`

(which yields `epython.md`).

One nice feature of writing elisp using org-babel is that it makes
documentation and commentary a little easier. If you are going to
contribute to epython, please edit the main epython.org file and not
generated files like `README.md`.

# Requirements<a id="orgheadline2"></a>

You will need to install things like flymake and pyempt for this to
work properly.

# Usage<a id="orgheadline3"></a>

The main way to use `epython.org` is to place the `epython.org`
somewhere and call `(org-babel-load-file "/path/to/epython.org")` in
your emacs initialization files.

This as an old file and some more documentation is needed but it is
provided in the hope that it is still useful as is. Some useful
features of epython include:

1.  Typing `C-.` will push a doctest line from your python buffer
    into the the python interpreter. The easiest way to see this is
    to do the following:
    1.  Open a python file.
    2.  Type `C-x 1` to have only a single window open.
    3.  Type `C-c !` to open a python interpreter in the other window.
    4.  Put the point on a doctest line that starts with ">>>".
    5.  Type `C-.`
    6.  Your doctest line should get pushed into the python buffer. By
        repeating this, you can conveniently step through a doctest.
2.  Typing `C-c c` when the point is at the start of a function
    definition will auto-generate a comment string for that function.
3.  Typing `C-c y` when in a python interpreter will start the pdb
    debugger in post-mortem mode to debug the most recent exception.
4.  Typing `C-c e` in the python buffer with the point on the start
    of a doctest failure will generate an ediff showing the doctest
    mismatch.
5.  When flymake is running, using `C-c j` and `C-c k` will go to the
    previous/next flymake failure while `C-c l` will display what
    flymake finds objectionable on the current line.
6.  Typing `C-c p` will push the current buffer to python. This is
    useful to evaluate the buffer if it is set to run doctests with
    a line like

    ```
    if __name__ == '__main__':
        doctest.testmod()
    ```

# Other tips and tricks<a id="orgheadline4"></a>

You may also find `company-mode` and `company-jedi` useful for
auto-completion. Those are not python specific so they are not
explicitly included here but you may wish to install them (e.g., via
something like `M-x package-list-packages`) and then put something
like

    (global-company-mode 't)
    (add-to-list 'company-backends 'company-jedi)

somewhere in your emacs initialization files.
