Git
===

The Git version control system is an essential tool for developers. These files are opt-in. So Opal won't create a config file for you upon install.
Rather, it's recommended that you include them as needed. 

Git Config
----------

The ``~/opal/git/config`` file provides a good set of default settings, and
offers some configuration for a better user experience. For example, when you make a mistake with Git, people wonder "How do I undo it?" The truth is their isn't a single ``undo``  command. There is however, one (or more) commands to do the opposite operation. They just depend upon the context. The git ``undo`` alias will perform a ``checkout`` to overwrite your local changes for a file. Deleting local changes that haven't yet been committed is one scenario Git can't reverse. The ``unstage`` alias removes the changes from the index, and puts them back into your working copy. In short, this undoes your `git add` for a file.

The git ``datelog`` and ``graph`` aliases help with showing you the commit history. The git ``info`` alias shows you the repositories you're connected to. Typically, just the origin is displayed. 

The git ``last`` alias will show the latest commit on the current branch. The ``stat`` alias will show the status of the files as a shortened format. This format provides a less noisy display of your ``git status``.


Commit Template
---------------

The ``~/opal/git/commit-template`` file helps you in crafting great commit messages, this commit template was created. The comments within the template serves as a reminder. Allow me to explain a couple of aspects that aren't so obvious.

The long, dashed line at the top of the comment is an indicator. This line
is 72 characters long. So if the body of your commit message extending past
the end of this line, you should make it shorter. Ideally, your editor will help you by wrapping lines automatically. If your editor doesn't have git commit support, this line still serves as a guide for you, the human.

Another aspect of the indicator line, is the ``@`` (at-symbol). This marks
the 50th character of the line. This indicaters where the subject line should end. 

Its generally a good idea to include the issue ``<ID>`` of your ticket. GitHub requires you to procede your issue number with  a ``#`` (hash symbol). Other systems like Jira don't use it.

For Github

.. code-block:: text 

    Issue: #123 

For Jira

.. code-block:: text 

    Issue: JRA-123 


Here's the complete git commit template.

.. code-block:: text 

    Subject line to say what you did
    
    Describe why you made this change. What was the motivation?
    
    Issue: <ID>
    
    #------------------------------------------------@----------------------
    # 
    #  * Write the subject line to sound like an authoritative command
    #  * Capitalize the subject line
    #  * Limit the subject line to 50 characters
    #  * Do not end the subject line with a period
    #  * Separate the subject from the body with a blank line
    #  * Use the body to explain what and why vs. how
    #  * Wrap the body at 72 characters
    #  * Include the issue number you're working on
    # 
    #

