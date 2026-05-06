
Bash Prompts
============

This is a collection of functions to give you control over how prompts are
displayed in Bash. The Bash Shell provides 4 levels of prompt: $PS1, $PS2,
$PS3, and $PS4. Each of these functions affects only a single prompt level. So
you're free to mix and match them as you like. Prompt levels one and two are
easy enough to trigger from the command line. Levels three and four are best
demonstrated within a script. So test scripts have been provided in the
``~/opal/bash/`` directory, which are named ``ps3-example.bash`` and
``ps4-example.bash`` respectively. 

There was considered effort to provide few different prompt styles provided, to
anticipate the needs of most people. However, should you find that you want
something different, you can make your own prompt functions. You can copy the
desired Opal function. Just remember to use your own namespace. 


PS1: The Primary Prompt
-----------------------

PS1 is an environment variable that holds the value of your primary prompt.
This is the primary prompt that you interact with on the command line. It's the
most most visible of the 4 prompts that Bash provides. In fact, many people
tend to forget that they can customize the other prompts.

opal:ps1_brief
^^^^^^^^^^^^^^

This style of prompt is quite common. It shows the username, name, and the base
directory. The home directory is displayed as a ``~`` (tilde). If you're a Git
user, the branch name is also included after the directory. There's a design assumption that a dark
terminal theme is being used when color is past as an argument. The default is
to use text formatting like bold or underline . 

@param style Optional.
   The value ``color`` is currently the only option.

.. code-block:: text

   username@host ~ $

opal:ps1_brief_light
^^^^^^^^^^^^^^^^^^^^

This is the light theme companion to ``opal:ps1_brief``. The structure is the
same.

.. code-block:: text

   username@host ~ $


opal:ps1_default_dark
^^^^^^^^^^^^^^^^^^^^^

This style of prompt uses two lines. Most people use a single user account on a
single machine. Due to this idea, the username and hostname are not included in
the prompt. The prompt starts with the time in 24-hour format. This is followed
by the base directory name. A ``~`` (tilde) will be used to represent the home
directory. This relies upon a dark terminal theme being used. The final piece
of data is the history number. 

On the second line, there is only the ``$`` (dollar symbol) which shows that
you're a normal user. This will be changed to a ``#`` if you're root. The nice
this about this style of prompt, is that it provides some detail about your
session, while providing a lot of space for you to write your command. 

.. code-block:: text

   13:00:34> directory-name> 849>
   $

opal:ps1_default_light
^^^^^^^^^^^^^^^^^^^^^^

This is the light theme companion to ``opal:ps1_default_dark``. The structure is the
same.

.. code-block:: text

   13:00:34> directory-name> 849>
   $


opal:ps1_developer
^^^^^^^^^^^^^^^^^^

This prompt provides the most information to the user. Sometimes a git branch
name can be quite long. With that in mind, this prompt style displays the
current git branch on the top line when available. The second line displays the
common ``username@hostname`` pattern. The third line displays the current date
and time using the ``opal-datetime`` format, followed by the directory base name.

.. code-block:: text

   git-branch-name
   useranme@hostname
   2026 Apr 30 Thu 16:24 directory-name
   $

opal:ps1_developer_light
^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: text

   git-branch-name
   useranme@hostname
   2026 Apr 30 Thu 16:24 directory-name
   $


opal:ps1_minimal
^^^^^^^^^^^^^^^^

A minimal prompt that shows the current working directory with $HOME abbreviated
with a tilde. The history number of this command is shown for ease of command reuse.
The $ symbol is used to reflect you're a normal user, where the # is used for root.

The username and hostname are not shown in this prompt because the most common
use case is for a person to always use their personal account on their own machine.
Also the git branch is not used in this prompt.

.. code-block:: text 

   dirname 842:$>


PS2: The Continuation Prompt
----------------------------

Unofficially, I call this the continuation prompt. This can be triggered when
using the ``\`` at the end of a line. If you open a string with a single or
double quote, and press `return`, this will also trigger the continuation
prompt.  This tells Bash that you're not done writing the current command. Bash
will give you a new line to keep appending to the current command.

opal:ps2_default_dark
^^^^^^^^^^^^^^^^^^^^^

This prompt is designed to connect with ``opal:ps1_default_dark``, so that it
looks like a continuation of the PS1 command. So it's purposefully minimal.

.. code-block:: bash 

   $ >

opal:ps2_default_light
^^^^^^^^^^^^^^^^^^^^^^

This is the light theme companion to ``opal:ps2_default_dark``.

.. code-block:: bash 

   $ >

PS3: The Selection Prompt
-------------------------

The selection prompt, which is used when presenting a list of choices.


opal:ps3_default
^^^^^^^^^^^^^^^^

.. code-block:: bash

   Choose a #> 

opal:ps3_minimal
^^^^^^^^^^^^^^^^

.. code-block:: bash

   Select:  

PS4: The Debug Prompt
---------------------

The debug prompt, helps you understand what is happening when scripts run. It
gets displayed when execution trace is enabled. Every line of the script is
displayed to you the line of code it's about to execute. Then it executes, and
displays the output. How much detail is in the prompt is up to you. Opal offers
you three PS4 prompt styles.



opal:ps4_default
^^^^^^^^^^^^^^^^

This prompt function tries to help you by vertically displaying of function
name file, and line number for each line of the script executed.

.. code-block:: text

   source-file: path/to/example.bash
   Function: your_function_name
   Line: 54
   >  


opal:ps4_minimal
^^^^^^^^^^^^^^^^

This prompt function tries to help you by displaying on a single chevron  
for each line of the script executed.

.. code-block:: text

   >  

opal:ps4_simple
^^^^^^^^^^^^^^^

This prompt function tries to help you by displaying on a single line, the 
filename and line number for each line of the script executed.

.. code-block:: text

   path/to/example.bash:54> 

