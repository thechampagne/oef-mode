

oef-mode
========

provide oef-mode (Online Exercise Format for wims) to emacs  

Features (Non-exhaustive)
-------------------------

* Syntax highlighting 
* Automatic indentation
* Connection to a wims session
* OEF Menu with:
    - Examples
    - Useful Characters Shortcuts
    - OEF Commands and Keywords
 
Requirements
------------

- Emacs 24.4+

Installation
------------

oef-mode available on [MELPA](http://melpa.org/). Add the following to
your emacs config file somewhere (.emacs, init.el, whatever):

```
(require 'package)
(add-to-list 'package-archives
             '("melpa" . "https://melpa.org/packages/") t)
```

Then use `M-x package-install RET oef-mode RET` to install the package.
 
Development
-----------

Before developing this package please remove it from Emacs if it was
installed before. You'll need [Cask][cask] to install the dependencies.

I usually use the following workflow when I develop this package:

1. `$ git clone https://github.com/raoulhatterer/oef-mode.git && cd oef-mode`;
2. `$ cask install`;
3. `$ cask exec emacs`;
4. `M-x find-file RET /path/to/oef-mode.el/oef-mode.el RET`;
5. `M-x eval-expression RET (add-to-list 'load-path default-directory) RET`;
6. `M-x eval-buffer RET`;
7. `M-x find-file RET /path/to/oef-mode.el/exemple.oef RET`;
8. Change something in the source code;
9. Go to the step `6`.

Licence
-------

Totally GPL




[cask]: http://cask.readthedocs.org/en/latest/
