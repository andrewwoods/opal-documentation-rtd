
Bash Clocks
===========

What time is it? There are many sources you can check to find the answer. Opal
makes it a bit easier to display the current time in the different parts of the
world on the command line. The ``~/opal/bash/aliases-clocks.bash`` contains
many aliases defined for your convenience, but this list is not meant to be
comprehensive. Please use these examples to help define your own. Copy it into
your custom dotfiles, rather than updating Opal.

When you ran the install script, a clocks alias was added to your ``$HOME/.bashrc`` file.
That was provided as a starting point. You should update it to meet your needs.

This code shows a small sample of what's available.

.. code-block :: bash

    alias utc="TZ=UTC date '+%c -- Universal Time'"
    alias eastern="TZ=US/Eastern date '+%c -- US Eastern'"
    alias central="TZ=US/Central date '+%c -- US Central'"
    alias mountain="TZ=US/Mountain date '+%c -- US Mountain'"
    alias arizona="TZ=US/Arizona date '+%c -- US Arizona'"
    alias pacific="TZ=US/Pacific date '+%c -- US Pacific'"
    alias toronto="TZ=America/Toronto date '+%c -- Canada, Toronto'"
    alias vancouver="TZ=America/Vancouver date '+%c -- Canada, Vancouver'"
    alias winnipeg="TZ=America/Winnipeg date '+%c -- Canada, Winnipeg'"
    alias mexico_city="TZ=America/Mexico_City date '+%c -- Mexico, Mexico City'"
    alias us_clocks="eastern; central; mountain; arizona; pacific"
    alias na_clocks="eastern; central; mountain; arizona; pacific; _n; toronto; mexico_city; winnipeg; vancouver"


There's an alias for `us_clocks` but there isn't one for Canada-only timezones. 
So let's make our own now, eh?


.. code-block :: bash

   alias canada_clocks="vancouver; winnipeg; toronto"

When you execute the canada_clocks alias, you'll see output like this:

.. code-block :: bash

    Wed Oct 22 14:13:01 2025 -- Canada, Vancouver
    Wed Oct 22 16:13:01 2025 -- Canada, Winnipeg
    Wed Oct 22 17:13:01 2025 -- Canada, Toronto

