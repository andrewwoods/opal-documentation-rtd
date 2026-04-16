
Bash Directory
==============

Improve the UX of handling files with these directory-related functions.

opal:cdls()
-----------

change to a directory and list its content

@param String $directory

.. code-block :: bash

    $ opal:cdls ~/opal/bin

opal:mkcd()
-----------

make a directory, and then change to it.

@param String $directory

.. code-block:: bash

    $ opal:mkcd ~/src/to/project 


opal:xdg_data_dir()
-------------------

Return the path to the directory $XDG_DATA_HOME.

There is a single base directory relative to which user-specific data files
should be written. $XDG_DATA_HOME defines the base directory relative to which
user-specific data files should be stored.

@return string $directory

.. code-block :: bash

    data_dir="$(opal:xdg_data_dir)"

opal:xdg_state_dir()
--------------------

Return the path to the directory $XDG_STATE_HOME. 

$XDG_STATE_HOME defines the base directory relative to which user-specific
state files should be stored. 

@return string $directory

.. code-block :: bash

    data_dir="$(opal:xdg_state_dir)"

opal:xdg_cache_dir()
--------------------

Return the path to the directory $XDG_CACHE_HOME.

$XDG_CACHE_HOME defines the base directory relative to which user-specific
non-essential data files should be stored.

@return string $directory

.. code-block :: bash

    data_dir="$(opal:xdg_cache_dir)"


opal:data_dir()
---------------

Return the directory path to the opal subdirectory under $XDG_DATA_HOME.

@return string $directory

@see opal:xdg_data_dir

.. code-block :: bash

    data_dir="$(opal:data_dir)"

opal:state_dir()
----------------

Return the directory path to the opal subdirectory under XDG_STATE_HOME.

@return string $directory

@see opal:xdg_state_dir

.. code-block :: bash

    data_dir="$(opal:state_dir)"

opal:cache_dir()
----------------

Return the directory path to the opal subdirectory under XDG_CACHE_HOME.

@return string $directory

@see opal:xdg_cache_dir

.. code-block :: bash

    data_dir="$(opal:cache_dir)"


