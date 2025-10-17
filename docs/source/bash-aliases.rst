
Bash Aliases
============


These aliases are examples you might find useful for inspiration.

The diff alias below was created on Mac, so the options may mean something
different if you run Linux. On the Mac, these are the options::

    -b causes trailing blanks to be ignored, and other strings of blanks to compare equal.
    -B causes chunks that include only blank lines to be ignored.
    -s cuases diff to report files which are the same, which are otherwise not mentioned.
    -U number produce a unified diff with `number` lines of context.


.. code-block :: bash

    alias diff='diff -bBs -U 3'
    alias empty='opal:truncate'
    alias localip='ifconfig en0 | grep "inet " '
    alias myip="curl http://ifconfig.me"
    alias nocomment="grep -v '^\s*[#;\"]'"
    alias please='sudo'
    alias weather="curl wttr.in"

Should the diff alias not work for you, you have two options.
The first is to use the `unalias` command, to remove it. The second is to
redefine it, to create your own definition.

