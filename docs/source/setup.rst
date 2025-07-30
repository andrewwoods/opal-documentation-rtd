Setup
=====

.. _installation:

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
5. Move the file to your $HOME directory.
6. Extract the file `opal-master.zip`
7. Rename the new directory from `opal-master` to `opal`.

.. code-block:: console

   $ mv opal-master opal

8. Run the Install Script

.. code-block:: console

   $ ./opal/install.bash


Install via Git Clone
^^^^^^^^^^^^^^^^^^^^^

1. Visit the `Opal Github <https://github.com/andrewwoods/opal>`_ Repository.
2. Click the green "Code" button above the file list.
3. Click the "Download ZIP" text.
4. Copy the HTTPS URL `opal-master.zip` file to your system.
5. Open your Terminal
6. Clone the repo

.. code-block:: console

   $ git clone https://github.com/andrewwoods/opal.git

7. Run the Install Script

.. code-block:: console

   $ ./opal/install.bash

After Installation
^^^^^^^^^^^^^^^^^^

Begin by opening a new terminal window. You'll want to ensure the environment
is fresh. Reloading ~/.bashrc in your current terminal window may have
unexpected results.


**Want to improve your terminal UX?** If you're an iTerm2 user, you're in luck! You
can add the Opal Dark or Opal Light color palette to your current profile.
These palettes attempt to provide better accessibility by improving color
contrast by tweaking the default ANSI color values.

A backup of your ~/.bash_profile and ~/.bashrc files were created during the
installation process. As you manually copy things back in, this is a good time
to clean house. As you comb through your original config files, you get to
evaluate what it still worth keeping.

Update
------

TODO: Document the update process.

