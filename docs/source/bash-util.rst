
Bash Utility
============

General
^^^^^^^

opal:bash_intro()
#################

Write the file header bash comment to the top of a bash file. 

This is best used in a script for creating new files. The header currently
only writes the current timestamp to the header, so you know when the
file was created.

@param string $filename

@return void

.. code-block :: bash

    $ opal:bash_intro ~/.bashrc


opal:vim_intro()
################

Write the file header Vim comment to the top of a bash file. 

This is best used in a script for creating new files. The header currently
only writes the current timestamp to the header, so you know when the
file was created.

@param string $filename

@return void

.. code-block :: bash

    $ opal:bash_intro ~/.vimrc


opal:bash_heading_box()
#######################

Write the section heading box to a file

This is best used in a script for creating new files. The header currently
only writes the current timestamp to the header, so you know when the
file was created.

@param string $heading

@param string $filename

@return void

.. code-block :: bash

    $ opal:bash_heading_box 'My Heading' ~/.bashrc


opal:preamble()
###############

Write the system preamble to a file

This is best used in a script for creating new files. The header currently
only writes the current timestamp to the header, so you know when the
file was created.

@param string $heading

@param string $filename

@return void

.. code-block :: bash

    $ opal:bash_heading_box 'My Heading' ~/.bashrc

opal:xdg_data_dir()
###################

Return the path to the directory $XDG_DATA_HOME.

There is a single base directory relative to which user-specific data files
should be written. $XDG_DATA_HOME defines the base directory relative to which
user-specific data files should be stored.

@return string $directory

.. code-block :: bash

    data_dir="$(opal:xdg_data_dir)"

opal:xdg_state_dir()
####################

Return the path to the directory $XDG_STATE_HOME. 

$XDG_STATE_HOME defines the base directory relative to which user-specific
state files should be stored. 

@return string $directory

.. code-block :: bash

    data_dir="$(opal:xdg_state_dir)"

opal:xdg_cache_dir()
####################

Return the path to the directory $XDG_CACHE_HOME.

$XDG_CACHE_HOME defines the base directory relative to which user-specific
non-essential data files should be stored.

@return string $directory

.. code-block :: bash

    data_dir="$(opal:xdg_cache_dir)"


opal:data_dir()
###############

Return the directory path to the opal subdirectory under $XDG_DATA_HOME.

@return string $directory

@see opal:xdg_data_dir

.. code-block :: bash

    data_dir="$(opal:data_dir)"

opal:state_dir()
################

Return the directory path to the opal subdirectory under XDG_STATE_HOME.

@return string $directory

@see opal:xdg_state_dir

.. code-block :: bash

    data_dir="$(opal:state_dir)"

opal:cache_dir()
################

Return the directory path to the opal subdirectory under XDG_CACHE_HOME.

@return string $directory

@see opal:xdg_cache_dir

.. code-block :: bash

    data_dir="$(opal:cache_dir)"


opal:up()
#########

Navigate up the file system a number of directories. Default 1.

Often you want to travel up a numnber of directory levels. 

.. code-block :: bash

    ~/src/public/opal-documentation-rtd $ opal:up 2

    ~/src/ $ 


opal:type_file()
################

Dynamically display a text file. 

An animated version of echo. Gives the sense of typing the file text to STDOUT.

@see bin/typer

.. code-block :: bash

   $ opal:type_file filename.txt


opal:type_line()
################

Dynamically display a line of text. 

An animated version of echo. Gives the sense of typing the text to STDOUT.

@see bin/typer

.. code-block :: bash

   $ opal:type_line "Hello World"


opal:spacer()
#############

Create a number of blank lines. By default, creates a single blank line.

Sometime you need to create vertical white space.

@param int quantity 
  The number of blank lines to create. Default = 1. 

@return string 

.. code-block :: bash

    $ opal:spacer 4


Date-related
^^^^^^^^^^^^

opal:filedate_to_day()
######################

Sometimes, you need to know the day of the week for a given date.

Convert the output of `opal:today filename-date` and `opal:today filename-timestamp`
to a weekday. This is use for when you want to create a report title based on the
the use of dates.


@param string date 
    The date must be formtted in YYYY-mm-DD for YYYY-mm-dd-HH-MM-SS format 

@return string 

.. code-block :: bash

    $ opal:filedate_to_date 2026-03-25 
    Wed


opal:monday_date()
##################

Monday is the first day of the current week. Get Monday's date.

@return string 

.. code-block :: bash

    $ opal:monday_date # The current date is 2026 Mar 25 Wed 17:00
    2026 Mar 23 Mon
     


opal:sunday_date()
##################

Sunday is the last day of the current week. Get Sunday's date.

@param string $date_format

@return string 

@see opal:get_date_format

.. code-block :: bash

    $ opal:sunday_date # The current datetime is 2026 Mar 25 Wed 17:00
    2026 Mar 29 Sun
     
opal:cal3()
###########

Display a current 3-month span. The previous month, current month, and the next
month. The output display horizontally.

.. code-block :: bash

        February 2026      
    Su Mo Tu We Th Fr Sa  
     1  2  3  4  5  6  7  
     8  9 10 11 12 13 14  
    15 16 17 18 19 20 21  
    22 23 24 25 26 27 28  
                          
                          
         March 2026       
    Su Mo Tu We Th Fr Sa  
     1  2  3  4  5  6  7  
     8  9 10 11 12 13 14  
    15 16 17 18 19 20 21  
    22 23 24 25 26 27 28  
    29 30 31              
                          
         April 2026       
    Su Mo Tu We Th Fr Sa  
              1  2  3  4  
     5  6  7  8  9 10 11  
    12 13 14 15 16 17 18  
    19 20 21 22 23 24 25  
    26 27 28 29 30        
                      


opal:ncal3()
############

Display a current 3-month span. The previous month, current month, and the next
month. The output display vertically.

.. code-block :: bash

    $ opal:ncal3

        February 2026     
    Mo     2  9 16 23   
    Tu     3 10 17 24   
    We     4 11 18 25   
    Th     5 12 19 26   
    Fr     6 13 20 27   
    Sa     7 14 21 28   
    Su  1  8 15 22      
    
        March 2026        
    Mo     2  9 16 23 30
    Tu     3 10 17 24 31
    We     4 11 18 25   
    Th     5 12 19 26   
    Fr     6 13 20 27   
    Sa     7 14 21 28   
    Su  1  8 15 22 29   
    
        April 2026        
    Mo     6 13 20 27   
    Tu     7 14 21 28   
    We  1  8 15 22 29   
    Th  2  9 16 23 30   
    Fr  3 10 17 24      
    Sa  4 11 18 25      
    Su  5 12 19 26      


opal:greeting()
###############

Greet the user based on the time of day.

@return string $greeting

@see opal:preamble

.. code-block :: bash

    $ opal:greeting
    Good afternoon 

opal:mach()
###########

Disable information about your system.

.. code-block :: bash

    $ opal:mach

User Experience
^^^^^^^^^^^^^^^

opal:country()
##############

Lookup a country name for a given 2-letter or 3-letter country code.

.. code-block :: bash

    $ opal:country ca
    Looking up CA ...
    CANADA
        
opal:define()
#############

Lookup the definitions for an English word using dict.org

.. code-block :: bash

    $ opal:define computer


opal:say_done()
###############

Use Mac's say command to convert simple message to sound.

By default, the message will say "It is Done!". This is useful when completing
a long running command, and you don't want to stare at your terminal.


.. code-block :: bash

    $ opal:say_done 

    $ opal:say_done "The scripts has completed" 



opal:show_dotfiles()
####################

Allow you to turn on and off the display of hidden files in Apples Finder.

Note: This doesn't affect the ls command.

@param string $choice
    Can be on, off, true, or false

@return void

.. code-block :: bash

    $ opal:show_dotfiles yes 

    $ opal:show_dotfiles no 



