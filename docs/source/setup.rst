Setup
=====

Opal is designed to be simple to use, and easily extendable. The heart of Opal
is Bash. There's also some value for Neovim, Vim, and Git users that one can
opt into. If you're someone that loves to live on the command line, then it
should be easy to create the experience you want for yourself. Natively, Bash
doesn't make it easy. So Opal has a wealth of functions to provide things you
might want.

Upon installation, a ``~/.bashrc`` and  a ``~/.bash_profile`` will be created
for you. The recommendation is to use the these versions as a foundation and
copy commands from your original versions into these. You might find that some
of the things, you've previously added to your dotfiles are no longer needed.


About the Installation
----------------------

Upon successsful installaion of Opal, three conditions will be met:

1. The opal framework will be installed into `$HOME/opal/`

2. Existing configuration files for specific locations will be backed up. The
   current file will be given a new name in the same directory that includes
   the timestamp in unix seconds. e.g. `~/.bashrc` becomes
   `~/.bashrc.1733439725`

3. A new configuration file will be created that points to a corresponding file
   in the opal directory configuration file will be created that points to a
   corresponding file in the opal directory. For example `$HOME/.bashrc` will
   contain "file include" of `$HOME/opal/bash/bashrc.bash`.


Installation
------------

There are two installation methods — via file download and git clone. Most
people will want to use the file download method. This will provide you
greater control over the Opal version you're running. The second method -
git clone - is for developers who would like to contribute improvements to
the Opal Project

Install via File Download
^^^^^^^^^^^^^^^^^^^^^^^^^

This is the easiest method, recommended for most users.

1. Visit the `Opal Github <https://github.com/andrewwoods/opal>`_ Repository.
2. Click the green "Code" button above the file list.
3. Click the "Download ZIP" text.
4. Save the file `opal-master.zip` file to your system.
5. Extract the file `opal-master.zip`
6. ``cd opal-master``
7. Run the Install Script in your Terminal

.. code-block:: console

  $ ./install.bash

Install via Git Clone
^^^^^^^^^^^^^^^^^^^^^

This is the method for project contributors.

.. code-block:: console

  $ cd ~
  $ git clone https://github.com/andrewwoods/opal opal
  $ cd opal
  $ ./install.bash


After Installation
^^^^^^^^^^^^^^^^^^

Begin by opening a new terminal window. You'll want to ensure the environment
is fresh. Reloading `~/.bashrc` in your current terminal window may have
unexpected results.


**Want to improve your terminal UX?** If you're an iTerm2 user, you're in luck! You
can add the Opal Dark or Opal Light color palette to your current profile.
These palettes attempt to provide better accessibility by improving color
contrast by tweaking the default ANSI color values.

A backup of your main config files were created during the installation process
using the current UNIX epoch timestamp. As you manually copy things back in,
this is a good time to clean house. As you comb through your original config
files, you get to evaluate what it still worth keeping.

