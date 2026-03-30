
Bash Developer
==============

This is a collection of functions a developer may find interesting.


function opal:check_site()
##########################

Check if the site at $url is up. 

This function uses curl to make the request. Each time it checks, an indicator
is printed to the screen. Be kind to systems. 

@param string $url

@param int $check_interval The number of seconds to wait to check again.
    Default = 60 seconds.

@return void

@uses curl

.. code-block:: bash

    $ opal:check_site 'http://example.com'

    $ opal:check_site 'http://example.com' 300



function opal:http_status()
###########################

This function checks a local file for a user-provided status code for it's title .

@param int $status_code

@return string

@uses grep

.. code-block:: bash

    $ opal:http_status 307
    307:Temporary Redirect
      The resource resides temporarily at a different URI, but keep using this one since it MAY change on occasion
 
    see https://www.rfc-editor.org/rfc/rfc9110.html#name-status-codes


function opal:parse_git_branch()
################################

Extract the name of the current git branch.

This is used primarily by opal functions that manage the display of PS1. 

@return string $branch_name

@uses git branch

.. code-block:: bash
    
    branch="(opal:parse_git_branch)"


function opal:trace_url()
#########################

Unfurl a URL to discover it's final location

Pass  a URL to this function and  you'll see all the output that cUrl 
receives for each request. This is particularly useful for short urls
from sites like bitly.com

@param string $url
  The web address of the link you want to explore.

@uses curl

.. code-block:: bash
    
    $ opal:trace_url https://example.com/asdf 


