
Bash Core
=========

`core.bash` serves as the main Opal file. **It's the only required file.** All
the others create a nicer experience. When you want to create a custom script,
and don't need the entire framework, you can include only this file.

.. code-block:: bash

  #!/usr/bin/env bash
  source ~/opal/bash/core.bash


Export Variables
----------------

.. code-block:: bash

    export OPAL_VERSION="3.0.0-beta"

    # The $OPAL_CONFIG_DIR is not meant to replace the XDG_CONFIG_HOME directory.
    # Rather it's an additional directory - one that could be used in the
    # XDG_CONFIG_DIRS list of directories.
    export OPAL_CONFIG_DIR="${OPAL_DIR}/config"

    # This makes the log file accessible as a variable. However, it's preferred that
    # the opal:data_dir, opal:state_dir, opal:cache_dir and opal:config_dir
    export OPAL_XDG_STATE_HOME="${XDG_STATE_HOME:-$HOME/.local/state}/opal"
    export OPAL_LOG_FILE="${OPAL_XDG_STATE_HOME}/error.log"


OPAL_DIR
^^^^^^^^

The `OPAL_DIR` holds the Opal install directory. This should be directly under your `$HOME` directory. Opal was designed so that $HOME/opal is where it resides.

OPAL_CONFIG_DIR
^^^^^^^^^^^^^^^

The `OPAL_CONFIG_DIR` is a supplemental configuration directory. It's how the
project can provide support for third party applications. This is a "top
level" directory, and each supported application has a subdirectory. The
primary purpose is to allow you to get setup faster by providing a solid,
simple foundation. Should you find yourself wishing that the configuration was
different. Don't change these configuration files. Instead, create a copy of
these files, and put it in your dotfiles project.  


Functions
---------

The core file `core.bash` contains all the essential functions of the Opal
framework. There are several Bash files that make up Opal, but `core.bash` is
meant to provide the foundation. One reason this is important, is becuase you
might want to create your own Bash app. Loading just this file makes it easy
for you to create while keeping things small, without having to override
different parts of the framework. 

This file is divided into multiple sections. Each sections contains multiple
functions.

General
^^^^^^^

opal:version()
##############

    Display the current version of the Opal framework. Uses the OPAL_VERSION variable.

    @return void

.. code-block:: bash

    $ opal:version
    Opal version: 3.0.0-beta-0406
    Bash version: 3.2.57(1)-release


opal:about()
############

    Display notice about what Opal is, where to find the repo, and copyright notice.

    @return void

.. code-block:: bash

    $ opal:about
    Opal version: 3.0.0-beta
    Bash version: 3.2.57(1)-release
    
    Opal is a command line framework. It's a foundation to provide a consistent
    foundation across machines and users. It's meant to be extended. Version 3
    improves the scripting experience.

    For the most up-to-date version, and the full documentation, visit the
    Github repo at https://github.com/andrewwoods/opal

    Copyright (C) 2023-2026 Andrew Woods



opal:std_error
##############

    Use this to write a message to Standard Error. This makes it easier for
    people to write an error message that can be redirected.

    @param string $message
        The user-facing error message 

    @return void
        The same message but redirected to STDERR

.. code-block:: bash

    $ opal:std_error "Something went wrong"


opal:std_log
############

    Use this to write a message to Standard Error and to the log. This makes it
    easier for people to write an error message on the command line.

    @param string $message
        The user-facing error message 

    @return void
        The same message but redirected to STDERR

Write a custom log message when your script fails.

.. code-block:: bash

    $ script.sh || opal:std_log "Write a custom log message."

Inside of a function, you might call it like this

.. code-block:: bash

    if opal:is_unset $1; then
        opal:std_log "You forgot to specify a parameter" 
        return 1
    fi


opal:is_set
###########

    Check to see if a value is present. 

    This is a wrapper function for Bash's ``-n`` check. The value has a length
    greater than zero.  
    

    @param string|int $value
        The user's content

    @return bool
        
.. code-block:: bash

    name="World"
    if opal:is_set "$1"; then
        name="$1"
    fi
    echo "Hello $name"


opal:is_unset
#############

    Check to see if a value is not present. 

    This is a wrapper function for Bash's `-z` check. A null or empty string will return true.

    @param string|int $value
        The user's content 

    @return bool

.. code-block:: bash

    if opal:is_unset "$1"; then
        opal:std_error "Please specify a value"
        return 1
    fi

opal:is_empty
#############

    An enhancement of opal:is_unset

    A null or empty string will return true. This function additionally trims
    whitespace from both ends of the input for comparison. So a string
    consisting entirely of whitespace will evaluate true.  

    @param string $value

    @return bool

.. code-block:: bash

    if opal:is_unset "$1"; then
        opal:std_error "Please specify a value"
        return 1
    fi


opal:success()
##############

    Write a success message written in a bright green color. 

    @param string $message
        The user-facing error message 

    @return string
        The same message wrapped in terminal escape codes

.. code-block:: bash

    opal:success "This is your message"


opal:failure()
##############

    Write a failure message written in a bright red color. 

    @param string $message
        The user-facing error message 

    @return string
        The same message wrapped in terminal escape codes

.. code-block:: bash

    opal:failure "This is your success message"

opal:message()
##############

    Write a informational message written in a bright cyan color. 

    @param string $message
        The user-facing info message 

    @return string
        The same message wrapped in terminal escape codes

.. code-block:: bash

    opal:message "This is your informational message"


opal:label()
############

    Write a label written in a bright yellow color. 

    @param string $message
        The user-facing error message 

    @return string
        The same message wrapped in terminal escape codes

.. code-block:: bash

    opal:label "This is your label"

opal:speak()
############

    Read out loud a string of text. Assumes the ``say`` command is installed. 

    @param string $message
        The user-facing content

    @return string
        The same message wrapped in terminal escape codes
    
    @uses say

.. code-block:: bash 

   opal:speak 'Would you like to play a nice game of chess?'

opal:ask()
##########

    Prompt the user with a statement and receive their input

    @param string $prompt
        What is your request of the user

    @return string
        the user input

    @uses opal:label

.. code-block:: bash

   $ answer="$(opal:ask "Would you like to play a nice game of chess?")"
   $ echo "The answer was $answer"


opal:sleep()
############

    Pause execution for a limited number of seconds. Default is 5 seconds.  

    This wraps the standard sleep command. The benefit is to tell you how long
    it will sleep. It also prevents execution from sleeping forever, by ensuring
    a default value is provided.

    @param int $seconds
        

    @return string
        The same message wrapped in terminal escape codes

.. code-block:: bash

    $ opal:sleep
    Using default value.
    Sleeping for 5 seconds

    $ opal:sleep 3
    Sleeping for 3 seconds

Conditionals
^^^^^^^^^^^^

Bash treats comparison for strings differently than for numbers. So there are
different operators that are used.

These functions are made to provide wrappers to Bash's handling of equality,
which is not very intuitive. They're meant to improve the developer experience.
Part of this effort is to not use abbrevation is function names. This increases
readability and understanding. For example, the name ``number_at_least`` is a
simpler way of saying ``greater than or equal to`` without abbreviation. 


Bash by default treats strings as case-sensitive.

opal:str_equals
###############

Provides a function to check for string equality. 

@param string 

@param string 

@returns bool

.. code-block:: bash

    fruit="Apple"

    #
    # Bash Native logic
    #
    if [[ $fruit == "Apple" ]]; then
        echo "Apple is the fruit of the month" 
    fi

    #
    # With Opal, the conditional can now expressed like this
    #
    if opal:str_equals "$fruit" "Apple"; then
        opal:success "Apple is the fruit of the month" 
    fi

opal:str_unequals
#################

A common pattern is to use negation to flip the truth of a logicial expression. 
Borrowing from the previous example, we might write the following

@param string 

@param string 

@returns bool

.. code-block:: bash

    if ! opal:str_equals "$fruit" "Apple"; then
        opal:failure "Apple is not available" 
    fi

Opal provides a function to combine that logic into a single function name:
`str_unequals`. This is in the spirit of Perl's `unless` keyword.

.. code-block:: bash

    if opal:str_unequals "$fruit" "Apple"; then
        opal:failure "Apple is not available" 
    fi


opal:number_equals
##################

Check for the equality of two numbers.

@param integer 

@param integer 

@returns bool

.. code-block:: bash

    # 
    # Bash uses $? to expand to the exit status of the most recently 
    # executed command.
    #
    if opal:number_equals $? 0; then
        opal:success 'The command succeeded'
    else
        opal:failure 'The command failed'
    fi

    #
    # If you only wanted to check for failure, you can 
    # negate the condition.
    #
    if ! opal:number_equals $? 0; then
        opal:failure 'The command failed'
    fi


opal:number_at_least
####################

The name `number_at_least` is a simpler way of saying `greater than or equal to`,
and without using an abbreviation. 

@param integer $value 

@param integer $minimum

@returns bool

.. code-block:: bash

    #
    # In the shell, an exit status of 0 is zero. Any integer 1 or more represents
    # an error. 
    # 
    if ! opal:number_at_least $? 1; then
        opal:failure 'The command failed'
    fi

opal:number_is_above
####################

This is a simpler way to say greater than the minimum value. 

@param integer $value 

@param integer $minimum

@returns bool

.. code-block:: bash

    #
    # Check the current temperature.
    # 
    if opal:number_is_above $temp_f 86; then
        opal:message 'It is hot! A great day to watch a baseball game!'
    fi

opal:number_at_most
###################

This is a simpler way to say less than or equal to the maximum value. 

@param integer $value 

@param integer $maximum

@returns bool

.. code-block:: bash

    #
    # Check the current temperature.
    # 
    if opal:number_at_most $temp_f 32; then
        opal:message "It's freezing "
    fi


opal:number_is_below
####################

This is a simpler way to say less than a maximum value. 

@param integer $value 

@param integer $maximum

@returns bool

.. code-block:: bash

    #
    # Check the person's height.
    # 
    if opal:number_is_below $height_inches 48; then
        opal:message "You must be at least this tall (48 inches) to ride this ride"
    fi

opal:number_between
###################

Determine if a number is inclusively between a minimum and a maximum value. 

@param integer $value 

@param integer $minimum

@param integer $maximum

@returns bool

.. code-block:: bash

    #
    # Check the year an album was released.
    # 
    if opal:number_between $year_released 1980 1989; then
        opal:success "The album was released in the best decade"
    fi


opal:command_exists
###################

Check that a command exists on the system.

@param string $command_name 

@returns bool

@uses type command to perform the check

.. code-block:: bash

    #
    # Check if command exists.
    # 
    if opal:command_exists $command_name; then
        opal:success "The command is available. Go ahead and run it"
    fi

opal:function_exists
####################

Check that a bash function is available on the system.

@param string $function_name 

@returns bool

@uses type command to perform the check

.. code-block:: bash

    #
    # Check the function is loaded into the shell
    # 
    if opal:function_exists $function_name; then
        opal:success "The function is available. Go ahead and run it"
    fi

Logging
^^^^^^^

The ability to record errors about our code is important. Getting feedback about our code
is how we understand to make it better. Opal provides a collection of logging functions,
one for each of the eight syslog levels, defined in RFC 5424. 


opal:log
########

Write a message to the error log, including the log level. This does the actual
writing to the log file.


 @param string $level
   The logging level of the message. The RFC 5424 determines the levels.
   The level determines the importance of the message.

 @param string $message
   The message you want to write to the error log.

 @param string $filepath
   Optional. The log file $HOME/.local/state/opal/error.log will be
   if not specified.

.. code-block:: bash

   $ opal:log ERROR "Something went wrong"


opal:log_emergency
##################

Log an EMERGENCY-level message.

 @param string $message
   The message you want to write to the error log.

 @param string $filepath
   Optional. The log file $HOME/.local/state/opal/error.log will be
   if not specified.

 @uses opal:log

.. code-block:: bash

   $ opal:log_emergency "Something went very wrong. Fix it STAT!"

opal:log_alert
##############

Log an ALERT-level message.

 @param string $message
   The message you want to write to the error log.

 @param string $filepath
   Optional. The log file $HOME/.local/state/opal/error.log will be
   if not specified.

 @uses opal:log

.. code-block:: bash

   $ opal:log_alert "Something went very wrong. Please respond!"


opal:log_critical
#################

Log a CRITICAL-level message.

 @param string $message
   The message you want to write to the error log.

 @param string $filepath
   Optional. The log file $HOME/.local/state/opal/error.log will be
   if not specified.

 @uses opal:log

.. code-block:: bash

   $ opal:log_critical "Oh No! Something went very wrong!"

opal:log_error
##############

Log an ERROR-level message.

 @param string $message
   The message you want to write to the error log.

 @param string $filepath
   Optional. The log file $HOME/.local/state/opal/error.log will be
   if not specified.

 @uses opal:log

.. code-block:: bash

   $ opal:log_error "An error has occurred!"

opal:log_warning
################

Log an WARNING-level message.

 @param string $message
   The message you want to write to the error log.

 @param string $filepath
   Optional. The log file $HOME/.local/state/opal/error.log will be
   if not specified.

 @uses opal:log

.. code-block:: bash

   $ opal:log_warning "An error has occurred!"

opal:log_notice
###############

Log a NOTICE-level message.

 @param string $message
   The message you want to write to the error log.

 @param string $filepath
   Optional. The log file $HOME/.local/state/opal/error.log will be
   if not specified.

 @uses opal:log

.. code-block:: bash

   $ opal:log_notice "hrmm, that's weird"

opal:log_info
#############

Log an INFO-level message.

 @param string $message
   The message you want to write to the error log.

 @param string $filepath
   Optional. The log file $HOME/.local/state/opal/error.log will be
   if not specified.

 @uses opal:log

.. code-block:: bash

   $ opal:log_info "This is something you should know."

opal:log_debug
##############

Log an DEBUG-level message.

 @param string $message
   The message you want to write to the error log.

 @param string $filepath
   Optional. The log file $HOME/.local/state/opal/error.log will be
   if not specified.

 @uses opal:log

.. code-block:: bash

   $ opal:log_debug "A developer wanted to know this."

Time
^^^^

We often need to display dates and times differently, depending upon where you
are in the world. So it's helpful to have functions for improving the user
experience of manipulating dates and times.

These functions are in `Bash Datetime <bash-datetime.html>`_


File System
^^^^^^^^^^^

These functions are in `Bash System <bash-file-system.html>`_

