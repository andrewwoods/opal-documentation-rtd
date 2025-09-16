Bash
====

The Bash shell is the foundation for the Opal framework. With version 3 of
Opal, a scripting layer was added, designed to improve the experience of
writing Bash scripts. In some case, an opal function is just a friendly wrapper
around native Bash behavior. In others, new functionality is added.

This section of the Opal Documentation will describe the structure of the project
and provide you with guidance on how to use the Opal framework.

Files
-----

Bash uses two main configuration files - `~/.bashrc` and `~/.bash_profile` - to
configure the user experience. Typically, the operating system will provide you
with some minimal configuration. When Opal is installed, It will back up these
files, and replace them with a more structured version that loads Opal as a
dependency. That backup contains the current time in UNIX epoch seconds in the
filename.

Opal has a counterpart to each of the user configuration files.

bashrc.bash
^^^^^^^^^^^

The bashrc.bash file is read by your ~/.bashrc. It provides some suggested
functionality to help improve your experience.. Upon install, when your
~/.bashrc is created, an "include" of this file is provided. Since this file is
considered optional, you can choose to comment it out. 

bash_profile.bash
^^^^^^^^^^^^^^^^^

This provides some environmental settings. This is where you'll find some
popular exported varibles like PATH, XDG_CONFIG_HOME, and EDITOR. The
bash_profile.bash file is read by ~/.bash_profile


Functions
---------

The functions.bash file is a collection of general Opal functions. When a set
of functions gets big enough, they get moved to a separate file e.g. prompt
functions.  

Core
----


Date Time
^^^^^^^^^



Developer
^^^^^^^^^

This is a collection of functions a developer may find interesting.

File
^^^^

Improve the UX of handling files with these file-related functions.

Directory
^^^^^^^^^

Improve the UX of handling files with these directory-related functions.

Prompts
^^^^^^^

This is a collection of functions to give you control over how prompts are
displayed in Bash.

Strings
^^^^^^^

This is a collection of functions for handling strings in Bash.

System
^^^^^^

These functions interact with the operating system, and help


Util
^^^^

A set of functions for creating scripts where the content of the presention is
is the focus. The functions don't make use of the `opal:` namespace, they use
a leading `_` (underscore). This file is intentionally not loaded by Opal.



Aliases
-------

This is a small set of optional aliases. These make things a little easier to
use, as well as providing some inspiration.  

Clocks
^^^^^^

This file provides an alias for many timezones throughout the world.


