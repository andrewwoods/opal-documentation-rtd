Editors
=======

In Opal version 3, a great deal of Bash scripting features were added. However,
Opal is more than Bash. There is also support for the powerful editors Neovim
and Vim. The primary mechanism for support are modular configuration that you can
opt into.

Neovim
------

This `nvim` directory provides Neovim support using Lua configuration files.
ettings files, to help users get started quickly. To leverage these config files,
you should read up on the runtimepath setting in Neovim's documentation. In Neovim, 
read the docs using `:help runtimepath`. Long story short, do this.  

.. code-block:: bash

   # in ~/.bash_profile, add this
   XDG_CONFIG_DIRS="${OPAL_CONFIG_DIR}"

Once you've added that, now you just need to tell Neovim which Lua config files
to include in your configuration.

.. code-block:: lua

   vim.opt.rtp:prepend(vim.fn.stdpath("config_dirs"))

   -- In your init.lua specify which file to require
   -- With options.lua you'll  get a working interface
   require("options")


init.lua
^^^^^^^^

The init.lua file is read by nvim upon startup. It provides some suggested
functionality to help improve your experience. Upon install, when your
~/.config/nvim/init.lua is created, an "include" of this file is provided.
Since this file is considered optional, you can choose to comment it out.


Vim
---

This `vim` directory provides supplemental Vim support as a config directory for
Vim users that use Opal. In Vim 9.1 the support for XDG variables, is not as
robust as Neovim's. So we need to do things a little different. Here's a block
to add to your vimrc file. Each of the source files is optional, so you can comment
it out or remove it, if you don't want it. 

.. code-block:: vim

    "
    " In your ~/.vimrc
    "
    if (isdirectory($OPAL_CONFIG_DIR))
        source $OPAL_CONFIG_DIR/vim/options.vim
        source $OPAL_CONFIG_DIR/vim/keymaps.vim
        source $OPAL_CONFIG_DIR/vim/dates.vim
        source $OPAL_CONFIG_DIR/vim/abbr-diacritics.vim
        source $OPAL_CONFIG_DIR/vim/abbr-misspelled.vim
    endif


