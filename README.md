gld-whitelist-by-DNS-nodes
==========================

Add support for whitelisting by DNS nodes (IPv4 and IPv6) to plain vanilla gld.

Installation
------------

Unpack the original sources from http://www.gasmi.net/down/gld-1.7.tgz, or use
the local copy provided.

$ tar zxf gld-1.7.tgz

Apply the gld-1.7.1 patch.

$ cd gld-1.7
$ patch -p1 <../gld-1.7.1.patch
patching file cnf.c
patching file gld.conf
patching file gld.h
patching file greylist.c
patching file server.c
patching file sockets.c
patching file tables.mysql
patching file tables.pgsql
patching file table-whitelist.sql

Run configure and then issue a make.

$ ./configure
$ make

Done.
