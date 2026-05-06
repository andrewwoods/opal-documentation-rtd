

Bash Datetime
=============

Time is a difficult topic for developers. While we can't solve every
time-related problem, we can make it a bit easier. A set of functions work
together to simplify the experience.

If you're looking for a way to see an example of all the supported formats, run
the ``today.bash`` script. It's located in the ~/opal/bin directory, so it's already
in your PATH.

.. code-block:: text

   $ today.bash
   
    unix=1777160478
    opal-date=2026 Apr 25 Sat
    opal-datetime=2026 Apr 25 Sat 19:41
    opal-timestamp=2026 Apr 25 Sat 19:41:18-0400
    iso-date=2026-04-25
    iso-datetime=2026-04-25T19:41-0400
    iso-timestamp=2026-04-25T19:41:18-0400
    world-date=25/04/2026
    world-datetime=25/04/2026 19:41
    world-timestamp=25/04/2026 19:41:18-0400
    us-date=04/25/2026
    us-datetime=04/25/2026 7:41 PM
    us-timestamp=04/25/2026 7:41:18 PM -0400
    usa-date=April 25, 2026
    usa-datetime=April 25, 2026 7:41 PM
    usa-timestamp=April 25, 2026 7:41:18 PM EDT
    filename-date=2026-04-25
    filename-datetime=2026-04-25-19-41
    filename-timestamp=2026-04-25-19-41-18

opal:today
----------

    @param string $formatname
        the name containing the date style and precision separated by a hypen e.g. opal-datetime

    @return string $duration
        The date formatted according to the given style and format

    @uses opal:get_date_format

The ``opal:today`` function displays the current date/time based on the format.
By default, it uses the ``opal-datetime`` format. However, you specify a format
name as the first argument.

One common value you'll want to know, is the current time in UNIX time. The
``opal:today`` function takes a single parameter, which is the name of the
format. 

.. code-block :: bash

    $ opal:today unix
    1761157954

The other format names follow a pattern. An example is shown here. The
available formats and precision values are defined in the
``opal:get_date_format`` function.

.. code-block :: bash

    $ opal:today unix 
    1761163284

    $ opal:today opal-date
    2025 Oct 22 Wed

    $ opal:today opal-datetime
    2025 Oct 22 Wed 16:01

    $ opal:today opal-timestamp
    2025 Oct 22 Wed 16:01:24-0400


opal:someday
------------

    It translates a UNIX timestamp into a recognizable format.

    @param int $unix_time
        Number of seconds since 1970-01-01T00:00:00-0000

    @param string $formatname
        Optional. The name containing the date style and precision separated by a hypen e.g. opal-datetime

    @return string $duration    
        The date formatted according to the given style and format

    @uses opal:get_date_format

The ``opal:someday`` function is a companion to the ``opal:today`` function. When
you already have a UNIX timestamp, use ``opal:someday`` to display the
corresponding date in your preferred format. If the second parameter is not passed, the `opal:datetime` format will be used.

.. code-block :: bash

    $ opal:someday 1761163284 iso-timestamp
    2025-10-22T16:01:24-0400


opal:get_date_format
--------------------

    @param string $formatname
        the name containing the date style and precision separated by a hypen e.g. opal-datetime

    @return string $duration
        The date formatted according to the given style and format

    The `opal:get_date_format` provides a lookup to retrieve a date format by name.
    There are many formats for you to choose from. It provides some logic for the
    today and someday functions. 

.. code-block :: bash

    $ opal:today opal-date
    2025 Oct 22 Wed

The ``opal:get_date_format`` is the workhorse the date functions. It
centralizes the logic of the date style and precision values. Almost all format
names follow a predicatble pattern. This pattern is a combination of *style*
and *precision*. The style refers to how the date is formatted. The
precision values are ``date``, ``datetime``, and ``timestamp``. The timestamp
is normally the only one that includes the timezone to ensure maximum
precision, since one expects precision from a timestamp. In most common use
cases, the timezone isn't necessary.

The supported date styles are as follows:

* unix
* opal
* iso
* world
* us
* usa
* filename

The name ``unix`` is a singular format, as it works differently from the
others. It returns the number of seconds since the UNIX epoch
1970-01-01T00:00:00-0000.

The ``us`` date formats provide dates in the numeric ``mm/dd/yyyy`` format.
This is common in the United States, but this can cause confusion for 
an international audience.

.. code-block:: text

    $ today us-date
    04/25/2026

    $ today us-datetime
    04/25/2026  8:08 PM

    $ today us-timestamp
    04/25/2026  8:08:13 PM -0400

If you dislike the ambiguity of the ``us`` numeric style, the ``usa`` date
style provides clarity by spelling out the month name.   

.. code-block:: text

    $ today usa-date
    April 25, 2026

    $ today usa-datetime
    April 25, 2026  7:25 PM

    $ today usa-timestamp
    April 25, 2026  7:25:55 PM EDT


The following example uses the *Opal project preferred format*. Yes, I'm aware
of the `XKCD commentary about standards <https://xkcd.com/927/>`_ but there is
a good reason for this format. The Opal format is year first, which provides
same logical ordering as the ISO format, but displays in a more friendly
manner. The ``opal`` date style starts with the year, followed by the month
abbreviation, then the day of the month which includes the weekday
abbreviation. The result is a date value of a consistent length no matter the
time of year, for a given precision.

.. code-block:: text

    $ opal:today opal-date
    2025 Oct 22 Wed

    $ opal:today opal-datetime
    2025 Oct 22 Wed 14:51

    $ opal:today opal-timestamp
    2025 Oct 22 Wed 14:51:53-0400

Looking to use a day-first format? Try the `world` style

.. code-block :: bash

    $ opal:today world-date
    22/10/2025

    $ opal:today opal-datetime
    22/10/2025 14:51

    $ opal:today opal-timestamp
    22/10/2025 14:51:53-0400


opal:duration
-------------

    Calculate the difference between two timestamps and display a report. 

    **NOTE** The smaller of the two timestamps must be specified first.

    @param int $start_time
        The starting UNIX timestamp

    @param int $end_time
        The ending UNIX timestamp

    @return string $duration
        A report of the calculation

The `opal:duration` tells you the difference in time between two unix
timestamps.

.. code-block :: bash

    $ opal:duration 1761163284 1761165351
    0 years 0 days 0 hours 34 minutes 27 seconds

opal:interval_to_seconds
------------------------

    Get the number of seconds for a given quantity of time.
    
    Many tools use the number of seconds for their operation. It can be useful
    to know number of seconds in a duration of time. This function makes it easy
    to calculate time intervals like 3 days or 2 weeks.
    
    @param string $unit
        The unit of time you wish to convert to seconds.
        **Allowed values**: minutes, hours, days, weeks, months
    
    @param integer $quantity
        The number of time units time you wish to convert to seconds
    
    @return integer $seconds
        The calculation result in seconds

.. code-block :: bash

    $ opal:interval_to_seconds days 2
    172800


opal:epoch
----------

    Get the UNIX epoch seconds for a given date, assuming midnight.
    
    @param string $date
        The date formatted as YYYY-MM-DD

    @return integer $seconds
        The date represented in UNIX epoch seconds

.. code-block :: bash

    $ opal:epoch 2026-03-17 
    1773763125



