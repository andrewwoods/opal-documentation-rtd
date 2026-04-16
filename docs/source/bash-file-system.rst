
Bash System
==============

These functions interact with the operating system, and help improve the user
experience. 


opal:command_exists
-------------------

Check if the specified directory exists. It's simply a wrapper around Bash's
native file functionality. It'll evaluate True if file exists and is a
directory.

Check that a command is available on your system.

@return bool

@uses type

.. code:: bash

   if opal:command_exists "eza"; then
       eza --long  "$1"
   else
       ls "$1"
   fi


opal:dir_exists
---------------

Check if the specified directory exists. It's simply a wrapper around Bash's
native file functionality. 

@return bool

.. code:: bash

   if ! opal:dir_exists "$HOME/tmp"; then
       mkdir "$HOME/tmp"
   fi

opal:ensure_dir_exists
----------------------

There are times when it's necessary to be available when writing bash scripts.
This function creates it, if it's unavailable.

Create a directory if it doesn't exist

When you need a directory to be avaialable, this will create it if need be.

@return bool

@uses type

.. code:: bash

   opal:ensure_dir_exists "$HOME/tmp"

   

opal:file_exists
----------------

Check if the specified file exists. It's simply a wrapper for Bash native
functionality. It's much easier to remember this names versus a test operator.

@return bool

.. code:: bash

   if ! opal:file_exists "$HOME/tmp"; then
       mkdir "$HOME/tmp"
   fi

opal:symlink_exists
-------------------

Check if a symlink exists

@return bool

.. code:: bash

   if ! opal:symlink_exists "$HOME/symlink_name"; then
       opal:success 'The symlink "symlink_name" was found'
   fi

opal:file_has_read
------------------

Check if the current user can read a file. 

@param string $filepath
   
@return bool

.. code:: bash

   if opal:file_has_read "$filepath"; then 
      opal:success "File '${filepath}' has read permission"
   else
      opal:failure "The file '${filepath}' cannot be read"
   fi


opal:file_has_write
-------------------

Check if the current user can read a file. 

@param string $filepath
   
@return bool

.. code:: bash

   if opal:file_has_write "$filepath"; then 
      opal:success "File '${filepath}' has write permission"
   else
      opal:failure "The file '${filepath}' cannot be written"
   fi

opal:file_has_execute
---------------------

Check if the current user can execute a file. 

@param string $filepath
   
@return bool

.. code:: bash

   if opal:file_has_execute "$filepath"; then 
      opal:success "File '${filepath}' has execute permission"
   else
      opal:failure "The file '${filepath}' cannot be executed"
   fi

opal:file_has_set_uid
---------------------

Determine if the file has the Set UID bit set

@param string $filepath
   
@return bool

.. code:: bash

   if opal:file_has_set_uid "$filepath"; then 
      opal:message "File '${filepath}' has Set UID permission"
   fi

opal:file_has_set_gid
---------------------

Determine if the file has the Set GID bit set

@param string $filepath
   
@return bool

.. code:: bash

   if opal:file_has_set_gid "$filepath"; then 
      opal:message "File '${filepath}' has Set GID permission"
   fi
