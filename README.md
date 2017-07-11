<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#orgheadline1">1. Introduction</a></li>
<li><a href="#orgheadline2">2. Requirements</a></li>
<li><a href="#orgheadline3">3. Usage</a></li>
</ul>
</div>
</div>

# Introduction<a id="orgheadline1"></a>

This is an org-babel file for epython. Org-babel files can be turned
into elisp files via something like

`(org-babel-tangle-file "epython.org" "epython.el" "emacs-lisp")`

or markdown files (e.g., for github README.md files) via

`M-x org-md-export-to-markdown`

to produce `epython.el`. One nice feature of writing elisp using
org-babel is that it makes documentation and commentary a little
easier.

# Requirements<a id="orgheadline2"></a>

You will need to install things like flymake and pyempt for this to
work properly.

# Usage<a id="orgheadline3"></a>

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
