
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

.. code-block:: bash

    $ opal:bash_intro ~/.bashrc

The output is written to the filename passed. Here's an example of the output.

.. code-block:: bash

   #
   # Generator: Opal <https://github.com/andrewwoods/opal>
   # Date-Created: 2026 Apr 19 Sun 11:49
   # Author: your_username 
   #


opal:vim_intro()
################

Write the file header Vim comment to the top of a bash file. 

This is best used in a script for creating new files. The header currently
only writes the current timestamp to the header, so you know when the
file was created.

@param string $filename

@return void

.. code-block:: bash

    $ opal:bash_intro ~/.vimrc

The output is written to the filename passed. Here's an example of the output.

.. code-block:: vim

    "
    " Generator: Opal <https://github.com/andrewwoods/opal>
    " Date-Created: 2026 Apr 19 Sun 11:49
    " Author: your_username 
    "

opal:bash_heading_box()
#######################

Write the section heading box to a file

This utility for creating a section header is best used in a script for
creating new files.  

@param string $heading

@param string $filename

@return void

.. code-block:: bash

    $ opal:bash_heading_box 'My Heading' ~/.bashrc


opal:preamble()
###############

Display the system preamble 

Show the user some information to greet them when opening a new terminal.

@return string

.. code-block:: bash

    $ opal:preamble

opal:up()
#########

Navigate up the file system a number of directories. Default 1.

Often you want to travel up a numnber of directory levels. 

.. code-block:: bash

    ~/src/public/opal-documentation-rtd $ opal:up 2

    ~/src/ $ 


opal:type_file()
################

Dynamically display a text file. 

An animated version of echo. Gives the sense of typing the file text to STDOUT.

@see bin/typer

.. code-block:: bash

   $ opal:type_file filename.txt


opal:type_line()
################

Dynamically display a line of text. 

An animated version of echo. Gives the sense of typing the text to STDOUT.

@see bin/typer

.. code-block:: bash

   $ opal:type_line "Hello World"


opal:spacer()
#############

Create a number of blank lines. By default, creates a single blank line.

Sometime you need to create vertical white space.

@param int quantity 
  The number of blank lines to create. Default = 1. 

@return string 

.. code-block:: bash

    $ opal:spacer 4


Date-related
^^^^^^^^^^^^

opal:filedate_to_day()
######################

Sometimes, you need to know the day of the week for a given date.

Convert the output of ``opal:today filename-date`` and ``opal:today
filename-timestamp`` to a weekday. This is use for when you want to create a
report title based on the the use of dates.


@param string date 
    The date must be formtted in YYYY-mm-DD for YYYY-mm-dd-HH-MM-SS format 

@return string 

.. code-block:: bash

    $ opal:filedate_to_date 2026-03-25 
    Wed


opal:monday_date()
##################

Monday is the first day of the current week. Get Monday's date.

@return string 

.. code-block:: bash

    $ opal:monday_date # The current date is 2026 Mar 25 Wed 17:00
    2026 Mar 23 Mon
     


opal:sunday_date()
##################

Sunday is the last day of the current week. Get Sunday's date.

@param string $date_format

@return string 

@see opal:get_date_format

.. code-block:: bash

    $ opal:sunday_date # The current datetime is 2026 Mar 25 Wed 17:00
    2026 Mar 29 Sun
     
opal:cal3()
###########

Display a current 3-month span. The previous month, current month, and the next
month. The output is displayed vertically. The command ``cal -3`` can be used 
to display the calendars positioned horizontaly.

.. code-block:: bash

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
month. The output is displayed vertically. The command ``ncal -3`` can be used 
to display the calendars positioned horizontaly.


.. code-block:: bash

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

.. code-block:: bash

    $ opal:greeting
    Good afternoon 

opal:mach()
###########

Disable information about your system.

.. code-block:: bash

    $ opal:mach

.. code-block:: bash

    Machine information:
    Darwin Aerilon.local 22.6.0 Darwin Kernel Version 22.6.0: Tue Jul 15 08:22:28 PDT 2025; root:xnu-8796.141.3.713.2~2/RELEASE_X86_64 x86_64

    Users logged on:
    awoods   console  -  29Mar26 20days -
    awoods   s000     -  29Mar26 1day  -bash         ˇø    /bin/bash      
    awoods   s001     -  29Mar26 1day  -bash         ˇø    /bin/bash      
    awoods   s002     -  07Apr26     - tmux attach -t WRITE
    awoods   s025     -  Fri14   2days -bash         ˇø    /bin/bash    

    Current date :
    Sun Apr 19 15:09:42 EDT 2026

    Machine status :
    15:09  up 20 days, 23:49, 5 users, load averages: 1.49 1.61 1.65

    Filesystem status :
    Filesystem       Size   Used  Avail Capacity iused       ifree %iused  Mounted on
    /dev/disk1s4s1  1.8Ti   18Gi  1.4Ti     2%  356882  4290768130    0%   /
    devfs           201Ki  201Ki    0Bi   100%     696           0  100%   /dev
    /dev/disk1s2    1.8Ti  4.0Gi  1.4Ti     1%    1392 14840563680    0%   /System/Volumes/Preboot
    /dev/disk1s6    1.8Ti  4.0Gi  1.4Ti     1%       4 14840563680    0%   /System/Volumes/VM
    /dev/disk1s5    1.8Ti   74Mi  1.4Ti     1%     538 14840563680    0%   /System/Volumes/Update
    /dev/disk1s1    1.8Ti  421Gi  1.4Ti    23% 3743229 14840563680    0%   /System/Volumes/Data
    map auto_home     0Bi    0Bi    0Bi   100%       0           0  100%   /System/Volumes/Data/home
    /dev/disk1s4    1.8Ti   18Gi  1.4Ti     2%  455010  4290100123    0%   /System/Volumes/Update/mnt1



User Experience
^^^^^^^^^^^^^^^

opal:country()
##############

Lookup a country name for a given 2-letter or 3-letter country code.

.. code-block:: bash

    $ opal:country ca
    Looking up CA ...
    CANADA
        
opal:define()
#############

Lookup the definitions for an English word using dict.org

.. code-block:: bash

    $ opal:define computer


opal:say_done()
###############

Use Mac's say command to convert simple message to sound.

By default, the message will say "It is Done!". This is useful when completing
a long running command, and you don't want to stare at your terminal.


.. code-block:: bash

    $ opal:say_done 

    $ opal:say_done "The script has completed" 



opal:show_dotfiles()
####################

Allow you to turn on and off the display of hidden files in Apples Finder.

Note: This doesn't affect the ls command.

@param string $choice
    Can be on, off, true, or false

@return void

.. code-block:: bash

    $ opal:show_dotfiles yes 

    $ opal:show_dotfiles no 



