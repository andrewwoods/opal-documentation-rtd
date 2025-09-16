
Bash Core
=========

The `core.bash` function serves as the main Opal file. It's considered the only
required file. All the others create a nicer experience. When you want to
create a custom script, and don't need the entire framework, you can include
only this file.

.. code-block :: bash

  #!/usr/bin/env bash
  source ~/opal/bash/core.bash



Export Variables
----------------

.. code-block :: bash

    export OPAL_VERSION="3.0.0-beta"

    # The $OPAL_CONFIG_DIR is not meant to replace the XDG_CONFIG_HOME directory.
    # Rather it's an additional directory - one that could be used in the
    # XDG_CONFIG_DIRS list of directories.
    export OPAL_CONFIG_DIR="${HOME}/opal/config"
    export OPAL_DATA_DIR="${XDG_DATA_HOME:-$HOME/.local/share}/opal"
    export OPAL_STATE_DIR="${XDG_DATA_HOME:-$HOME/.local/state}/opal"
    export OPAL_LOG_DIR="${OPAL_STATE_DIR}"



OPAL_CONFIG_DIR
^^^^^^^^^^^^^^^

Write a description ofthe OPAL_CONFIG_DIR describing what it does, and why it's
important.


Functions
---------

The core file contains all the essential functions of the Opal framework.
The functions in here are the primary code dependency.

The contents of the core.bash are required for Opal. There are several Bash
files that make up Opal, but core.bash is meant to provide the foundation. One
reason you might want to use just this file is to create your own Bash app,
Loading just this file makes it easy for you to create, without having to
override different parts of the framework. 

This file is divided into multiple sections. Each sections contains multiple
functions.

General
^^^^^^^

function opal:version
#####################

Display the current version of the Opal framework. Uses the OPAL_VERSION
variable.

function opal:about
###################

Display notice about what Opal is, where to find the repo, and copyright notice.

opal:std_error
##############

Use this to write a message to Standard Error. This makes it easier for people 
to write a message

opal:is_set
###########

Check to see if a value is present. This is a wrapper function for Bash's `-n` check.

opal:is_unset
#############

Check to see if a value is not present. This is a wrapper function for Bash's `-z` check.


opal:success()
##############

Write a success message written in a bright green color. 

opal:failure()
##############

Write a failure message written in a bright red color. 

opal:message()
##############

Write a informational message written in a bright cyan color. 

opal:label()
############

Write a label written in a bright yellow color. 

opal:speak()
############

Here a string of text spoken instead of just displayed on the screen.

opal:ask()
##########



opal:sleep()
############

Conditionals
^^^^^^^^^^^^

opal:string_equals
##################

opal:string_unequal
###################

opal:number_equals
##################

opal:number_at_least
####################

opal:number_is_above
####################

opal:number_at_most
###################

opal:number_is_below
####################

opal:number_between
###################


opal:command_exists
###################

opal:function_exists
####################

Logging
^^^^^^^

There are several logging-related functions.

opal:log
########

Ohis is the opal:log function description

opal:log_emergency
##################

opal:log_alert
##############

opal:log_critical
#################

opal:log_error
##############

opal:log_warning
################

opal:log_notice
###############

opal:log_info
#############

opal:log_debug
##############


Time
^^^^

We often need to display dates and times differently, depending upon where you
are in the world. So it's helpful to have functions for improving the user
experience of manipulating dates and times.

opal:get_date_format()
######################

The `opal:get_date_format` provides a lookup to retrieve a date format by name.
There are many formats for you to choose from. It provides some logic for the
today and someday functions. 

opal:today()
############

The `opal:today` functions display the current date/time based on the format.
By default, it uses the `opal-datetime` format. However, you specify a format
name as the first argument.

opal:someday()
##############

The `opal:someday` is a sibling function to the `opal:today` function. It
translates a UNIX timestamp into a recognizable format. You specify a UNIX timestamp as the
first parameter, and a format name as the second argument.

opal:duration()
###############

The `opal:duration` tells you the difference in time between two unix timestamps.

opal:interval_to_seconds()
##########################

File System
^^^^^^^^^^^

opal:ensure_dir_exists
######################

opal:dir_exists
###############

opal:file_exists
################

opal:symlink_exists
###################

opal:file_has_read
##################

opal:file_has_write
###################

opal:file_has_execute
#####################

opal:file_has_set_uid
#####################

opal:file_has_set_gid
#####################

Unprocessed
^^^^^^^^^^^

.. code-block :: bash

   function opal:about_macos {
   function opal:about_macos_fallback {
   function opal:about_popos {
   function opal:about_popos_fallback {
   function opal:about_ubuntu {


