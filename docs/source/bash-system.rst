
Bash System
===========

These functions interact with the operating system, and help improve the user
experience. 

opal:bak 
--------

    Create a backup of a file or directory

    @param string $path 
      when path is a file, a copy is made with .bak appended to it's name. if
      path is a directory, a compressed tarball will be made of the directory

.. code-block:: bash

    # Create filename.txt filename.txt.bak
    $ opal:bak filename.txt
    
    # Create a backup of the wordpress directory.
    # wordpress.tar.gz gets created.
    $ opal:bak wordpress 


opal:extract 
------------

    "un-compress" a file from a variety of common formats

    @param String $filename 
      must be a common compressed file type like ZIP or Tar

.. code-block:: bash

    # Display lines 90 - 110. Line 100 is the middle line of content
    $ opal:numseg error.log 100
    
    # Display lines 100 through 140.
    $ opal:numseg error.log 100 140


opal:numseg 
-----------
    
    Display a numbered segment of a file
    
    When only the start_line is specified, a range of 10 lines before and after
    that line will be numbered and displayed. when start_line and end_line are
    specified, those lines and all those between will be numbered and displayed
    
    @param String $filename 
      the text file with the content

    @param Integer $start

    @param Integer $end
        Optional. The last
    
    Example:

.. code-block:: bash

    # Display lines 90 - 110. Line 100 is the middle line of content
    $ opal:numseg error.log 100
    
    # Display lines 100 through 140.
    $ opal:numseg error.log 100 140


opal:seg 
--------
    
    Display a segment of a file
    
    When only the start_line is specified, a range of 10 lines before and after
    that line will be displayed. When both $start and $end are specified, those
    lines and all those between will be displayed
    
    @param string $filename 
      the text file with the content

    @param integer $start

    @param integer $end
        Optional. The last line of the range
    
    Example:

.. code-block:: bash

    # Display lines 90 - 110. Line 100 is the middle line of content
    $ opal:seg error.log 100
    
    # Display lines 100 through 140.
    $ opal:seg error.log 100 140


opal:locate 
-----------

    Display the file path and line number where the function is defined.

    @param string $function_name
      the name of the function you want to find  

    @return 

.. code-block:: bash

    # Learn where the opal:today function is defined. 
    $ opal:locate opal:today 
    


opal:describe 
-------------

    Display the definition of a function.

    @param string $function_name
      the name of the function you want to display  


.. code-block:: bash

    # Learn where the opal:today function is defined. 
    $ opal:locate opal:today 

opal:show 
---------

    A wrapper around the declare command. Display all data of a specified type. 

    @param string $type
      the type of the information you want to display

      * arrays
      * defs
      * names
      * readonly
      * exports
      * integers


.. code-block:: bash

    # Display a list of all bash functions 
    $ opal:show names 

opal:swap 
---------

    Change the contents of two files

    This is useful when testing two different versions of a file, and the 
    filename is signicant to its operation. A config file is a good example.

    @param string $file_one
      the name of the first file to swap  

    @param string $file_two
      the name of the second file to swap  

.. code-block:: bash

    # Learn where the opal:today function is defined. 
    $ opal:swap file1.txt file2.txt 


opal:touchx 
-----------

    Make it easy and fast to create a file of a defined type

    Inspired by the touch command which creates an empty file. This helps
    create files with default content.

    @param string $filename
      the name of the file to create

    @param string $style
      the name of the second file to swap  

.. code-block:: bash

    # Create a GIt Keep file and make it executable.
    $ opal:touchx .gitkeep

    # Create a PHPinfo file file and make it executable.
    $ opal:touchx info.php phpinfo 

opal:truncate
-------------

    Remove the contents of a file

    There are times when you want the file to remain, but only clear out
    the contents. This is useful when dealing with large log files 
    taking up too much space.

    @param string $filename
      the name of the file to create

.. code-block:: bash

    # Remove the contents of a large file.
    $ opal:truncate error.log 




