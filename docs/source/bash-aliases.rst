
Bash Aliases
============


These aliases are examples you might find useful for inspiration.

.. code-block:: bash

    alias diff='diff -bBs -U 3'
    alias empty='opal:truncate'
    alias localip='ifconfig en0 | grep "inet " '
    alias myip="curl http://ifconfig.me"
    alias nocomment="grep -v '^\s*[#;\"]'"
    alias please='sudo'
    alias weather="curl wttr.in"

The `nocomment` alias is useful for displaying a file without the comments. The
main Apache config file (httpd.conf), is heavily commented. The remaining lines
appear much cleaner. You'll probably need to create a command to remove
multiple consecutive lines of white space. However, that is left as an exercise
for you dear reader. 

The diff alias was created on Mac, so the options may mean something different
if you run Linux. On the Mac, these are the options:
::

    -b causes trailing blanks to be ignored, and other strings of blanks to compare equal.
    -B causes chunks that include only blank lines to be ignored.
    -s cuases diff to report files which are the same, which are otherwise not mentioned.
    -U number produce a unified diff with `number` lines of context.

Should the diff alias not work for you, you have two options. The first is to
use the `unalias` command, to remove it. The second is to redefine it, to
create your own definition.

These alias provide an easier way to refer to commonly used functions. They can be found in the ~/opal/bash/bashrc.bash file. Should you prefer your own implementation, you can easily redefine the alias to point to it.

.. code-block:: bash

    alias bak="opal:bak"
    alias cdls="opal:cdls"
    alias desc="opal:describe"
    alias extract="opal:extract"
    alias mkcd="opal:mkcd"
    alias numseg="opal:numseg"
    alias seg="opal:seg"
    alias show="opal:show"
    alias today="opal:today"
    alias touchx="opal:touchx"
    alias up="opal:up"

    # @NOTE: the 'locate' command exists on many systems, hence the use of 'loc'
    alias loc="opal:locate"

