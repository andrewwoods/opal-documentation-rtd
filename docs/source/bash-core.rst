
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


General
^^^^^^^

function opal:version
#####################

function opal:about
###################


opal:std_error
##############

opal:is_set
###########

This describes the is_set function.

opal:is_unset
#############

This describes the is_unset function. It does the opposite.


opal:success()
##############

opal:failure()
##############

opal:message()
##############

opal:label()
############

opal:speak()
############

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

opal:get_date_format()
######################

opal:today()
############

opal:someday()
##############

opal:duration()
###############

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


