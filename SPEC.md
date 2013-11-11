YunoHost node
-------------

Modified Tahoe LAFS client/server that requests authorization before uploading a share (as a client), and check authorization before accepting a share (as a storage server).
Only immutable files are concerned (and allowed) for now.


Introducer
----------

Modified Tahoe LAFS introducer to publish and announce every registered and non-banned nodes.


Authorization server
--------------------

Simple Lua/Nginx service that manages authorizations between Tahoe nodes. Gives authorizations to non-banned nodes and checks available free-space in database.


Cron
----

Python cron that checks every Tahoe nodes of the grid regurlarily and randomly.
If a storage node becomes unavailable, it can ban it in databse so that its upload capability becomes disabled.

Database
--------

PostgreSQL database that list every nodes in the grid.
Rows :
* ID
* nodeID
* IP
* is_banned
* is_warned
