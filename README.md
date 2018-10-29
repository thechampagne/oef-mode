

oef-mode
========

provide oef-mode (Online Exercise Format for wims) to emacs  

Features (Non-exhaustive)
-------------------------

* Syntax highlighting 
* Automatic indentation
* Completion suggestions
* Connection to a wims session
* OEF Menu with:
    - Examples
    - Useful Characters Shortcuts
    - OEF Commands and Keywords
 
Requirements
------------

- Emacs
- Yafolding
- rainbow-mode
- emmet-mode
- rainbow-delimiters
- expand-region
- cl-li
- company-mode

Installation
------------

I would recommend El-get http://wikemacs.org/wiki/El-get to install oef-mode


#  GnuTLS must be available
So the idea is that you copy/paste this code into your *scratch* buffer:

    (gnutls-available-p)

hit C-j, and if you get 't' GnuTLS is available but if you get 'nil'  you have to install it.


## On Aquamacs

Usually user-specific customizations should go into ~/Library/Preferences/Aquamacs Emacs/Preferences.el
though El-get must be called before (package-initialize) yet customization.el contain (package-initialize)
we have to put user-specific customizations into customizations.el.

So :

- Edit  ~/Library/Preferences/Aquamacs Emacs/customizations.el  : 
- Copy- paste this code before (package-initialize):

        ;; for El-get
        (with-eval-after-load 'tls
          (push "/private/etc/ssl/cert.pem" gnutls-trustfiles))
        
        (add-to-list 'load-path "~/.emacs.d/el-get/el-get")
        (unless (require 'el-get nil 'noerror)
          (with-current-buffer
              (url-retrieve-synchronously
               "https://raw.githubusercontent.com/dimitri/el-get/master/el-get-install.el")
            (goto-char (point-max))
            (eval-print-last-sexp)))
        
        (add-to-list 'el-get-recipe-path "~/.emacs.d/el-get-user/recipes")
        (el-get 'sync)
        
        (package-initialize)

(The 2 first lines are a way to have GnuTLC working because Aquamacs doesn't support GNUTLS. )

- Save and restart Aquamacs.




Development
-----------

Before developing this package please remove it from Emacs if it was
installed before. You'll need [Cask][cask] to install the dependencies.
After cask installation I added in my `~/.profile` file:
```
# cask
 export PATH="/home/hatterer/.cask/bin:$PATH"
```

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
