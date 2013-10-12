Idea
====

Tahoe LAFS grid with filtered access. The only access points are helpers, with authentication. The grid is however only composed of storage/client servers: you have to be a storage server (and have a cID) to have access to the grid. A central database is storing every useful informations.


Components
----------
  - Tahoe LAFS (1.9.2 tested)
  - Subscribe server


Introducer
----------

Modified Tahoe LAFS introducer with tubID filtering

Method needed:
  - get_helpers_id_list: Fetch the helpers to announce them all the grid''s node (IP based auth)


Helper
------

Standard Tahoe LAFS helper


Storage/Client server
---------------------

Standard Tahoe LAFS node with stats_gatherer furl (see https://tahoe-lafs.org/trac/tahoe-lafs/browser/trunk/docs/stats.rst )


BCBG Client
-----------

Client of Web API

Methods needed (cID/pass auth):
  - list_files: get a list of your backups
  - put_file: upload a file to the grid via an helper
  - get_file: download on of your backup via an helper
  - delete_file: delete on of your backup via an helper


Database
--------

Standard PostreSQL database


Cron checker
------------

Python cron that check storage nodes stats, availability, consistency.

Method needed (IP based auth):
  - get_node_list: Get domain/ip of every node of the grid
  - warn_node: add a warning for a node (that is not a storage node or unavailable)


Web API
-------

TODO: Routes
