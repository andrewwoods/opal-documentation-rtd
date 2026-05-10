
Bash Strings
============

Dealing with strings is very common in writing code. But Bash is weird in the
way that it `works with strings
<https://www.commandinline.com/bash-string-manipulation-guide/>`_. You've
already seen the ``opal:str_equals`` and ``opal:str_unequals`` functions in the
:doc:`bash-core` file. You can read about string modification files below. 


opal:str_length
---------------

Returns the length of a string.

| **@param** *String* $title 
| 
| **@output** *Integer*


.. code-block:: bash

   $ opal:str_length "United States of America"
   24

   
opal:str_lower
--------------

Replace uppercase letters with lowercase letters.

| **@param** *String* $title 
| 
| **@output** *String*

.. code-block:: bash

   $ opal:str_lower "United States of America" 
   united states of america


opal:str_slug
-------------

Convert a string to a path friendly slug.

A slug consists of only letters, numbers, and hyphens so a string can be
safely used is situations like file paths and URLs. Optionally, you can
pass the second parameter to convert the slug to lowercase or uppercase.

| **@param** *String* $content
| 
| **@param** *String* $style
| Can be "lower" or "upper"
| 
| **@output** *String*
| 
| **@uses** sed
| 
| **@uses** iconv

.. code-block:: bash

   $ opal:str_slug "There's Something Happening Here."
   Theres-Something-Happening-Here

   $ opal:str_slug "There's Something Happening Here." lower
   theres-something-happening-here

   $ opal:str_slug "There's Something Happening Here." upper 
   THERES-SOMETHING-HAPPENING-HERE


opal:str_trim
-------------

Remove the spaces from the start and end of a string.

| **@param** *String* $title 
| 
| **@output** *String*
| 
| **@uses** iconv
| 
| **@uses** sed

.. code-block:: bash

   $ opal:str_trim " This  sentence  has A LOT of   extra spaces.  " 
   This  sentence  has A LOT of   extra spaces



opal:str_trimmer
----------------

Remove the spaces from the start and end of a string, and replaces multiple
internal spaces with a single space.

| **@param** *String* $title 
| 
| **@output** *String*
| 
| **@uses** *Opal:str_trim*
| 
| **@uses** sed

.. code-block:: bash

   $ opal:str_trimmer " This  sentence  has A LOT of   extra spaces  " 
   This sentence has A LOT of extra spaces


opal:str_upper
--------------

Replace lowercase letters with uppercase letters.

| **@param** *String* $title 
| 
| **@return** *String*
| 
| **@uses** tr

.. code-block:: bash

   $ opal:str_lower "United States of America" 
   UNITED STATES OF AMERICA


