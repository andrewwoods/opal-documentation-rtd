Bash
====

The Bash shell is the foundation for the Opal framework. With version 3 of
Opal, a scripting layer was added, designed to improve the experience of
writing Bash scripts. In some cases, an opal function is just a friendly
wrapper around native Bash behavior. In others, new functionality is added to
enhance the user experience. Also, an effort was made to increase flexibility
by providing XDG support.

This section of the Opal Documentation will describe the structure of the
project and provide you with guidance on how to use the Opal framework. You'll
notice that Opal looks quite different from most shell scripts. Each of these
functions uses the `opal:` prefix. This is to prevent collisions with other
shell functions. The functions in the Opal framework are also coded
defensively. Bash doesn't natively support argument checking. So steps are
taken to help guide you to pass the data directory. Bash natively separates
strings on whitespace. So to maintain strings between functions you'll need to
quote them more heavily that in other programming languages.

Should you find yourself wishing that a Opal worked differently, don't modify
it. Instead, you should copy the function into your dotfiles and update the
namespace to the string you use. The prefix `dot:` is recommended for your
personal dotfiles. *For example*, the `opal:data_dir` function creates a path
by using the output of `opal:xdg_data_dir` and appends the `/opal` subdirectory
onto it. You should copy it and name your version `dot:data_dir` and update the
logic to determine to which directory you want the data written.

Files
-----

Bash uses two main configuration files - `~/.bashrc` and `~/.bash_profile` - to
configure the user experience. Typically, the operating system will provide you
with some minimal configuration. When Opal is installed, It will back up these
files, and replace them with a more structured version that loads Opal as a
dependency. Don't panic! Your original is saved, and contains the current time
in UNIX epoch seconds in the filename. It's recommended that you copy anything
you want to keep into your new configuration files.

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


Organization
------------

The majority of the Bash component is a collection of functions organized by
subject. The functions use an `opal:` namespace, meaning each function name
starts with it. This helps provide clarity, and prevents accidental
redefinition of any existing functions. These functions can be used in bash
scripts or directly on the command line. One essential function is `opal:show`
takes a single parameter. Calling `opal:show names` will display a list of
functions loaded in your shell.

.. code-block:: bash

    $ opal:show names

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


