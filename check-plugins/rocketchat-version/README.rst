Check rocketchat-version
=========================

Overview
--------

This plugin lets you track if a Rocket.Chat server update is available. To check for updates, this plugin uses the Git Repo at https://github.com/RocketChat/Rocket.Chat/releases. To compare against the current/installed version of Rocket.Chat, the check needs URL/API access to the Rocket.Chat server.


Fact Sheet
----------

.. csv-table::
    :widths: 30, 70

    "Check Plugin Download",                "https://github.com/Linuxfabrik/monitoring-plugins/tree/main/check-plugins/rocketchat-version"
    "Check Interval Recommendation",        "Once a day"
    "Can be called without parameters",     "No"
    "Compiled for",                         "Linux, Windows"
    "Requirements",                         "Requires a user with strong password and 'view-statistics' permission (only)."
    "Uses SQLite DBs",                      "Yes"


Help
----

.. code-block:: text

    usage: rocketchat-version [-h] [-V] [--always-ok]
                              [--cache-expire CACHE_EXPIRE] [--insecure]
                              [--no-proxy] -p PASSWORD [--timeout TIMEOUT]
                              [--url URL] --username USERNAME

    This plugin lets you track if server updates are available. Requires a user
    with strong password and "view-statistics" permission (only).

    options:
      -h, --help            show this help message and exit
      -V, --version         show program's version number and exit
      --always-ok           Always returns OK.
      --cache-expire CACHE_EXPIRE
                            The amount of time after which the update check cache
                            expires, in hours. Default: 24
      --insecure            This option explicitly allows to perform "insecure"
                            SSL connections. Default: False
      --no-proxy            Do not use a proxy. Default: False
      -p, --password PASSWORD
                            Rocket.Chat API password.
      --timeout TIMEOUT     Network timeout in seconds. Default: 3 (seconds)
      --url URL             Rocket.Chat API URL. Default:
                            http://localhost:3000/api/v1
      --username USERNAME   Rocket.Chat API username. Default: rocket-stats


Usage Examples
--------------

.. code-block:: bash

    ./rocketchat-version --username rocket-stats --password mypassword --url http://rocket:3000/api/v1 --cache-expire 8 --always-ok
    
Output:

.. code-block:: text

    Rocket.Chat v6.6.2 installed, Rocket.Chat v6.6.3 available


States
------

* If wanted, always returns OK,
* else returns WARN if update is available.


Perfdata / Metrics
------------------

There is no perfdata.


Credits, License
----------------

* Authors: `Linuxfabrik GmbH, Zurich <https://www.linuxfabrik.ch>`_
* License: The Unlicense, see `LICENSE file <https://unlicense.org/>`_.
