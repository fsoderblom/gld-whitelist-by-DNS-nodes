gld-whitelist-by-DNS-nodes
==========================

Add support for whitelisting by DNS nodes (IPv4 and IPv6) to plain vanilla gld.

Installation
------------

Unpack the original sources from http://www.gasmi.net/down/gld-1.7.tgz, or use
the local copy provided.

```
$ tar zxf gld-1.7.tgz
```

Apply the gld-1.7.2 patch.

```
$ cd gld-1.7
$ patch -p1 <../gld-1.7.2.patch
patching file cnf.c
patching file gld.conf
patching file gld.h
patching file greylist.c
patching file server.c
patching file sockets.c
patching file tables.mysql
patching file tables.pgsql
patching file table-whitelist.sql
```

Run configure and then issue a make.

```
$ ./configure
$ make
$ make install
```

Create a configuration file for gld as /etc/gld.conf,
an example config file is supplied as "gld.conf".

Create a pseudo user to run gld as.

```
$ sudo groupadd _gld
$ sudo useradd -c "& daemon" -g _gld _gld
```

Finally, use the supplied "gld.init" to create a sensible
startup file for gld in /etc/init.d/gld (for SysV based startup).

Start gld, by issuing the command "service gld start" as root.

Whitelisting
------------

To whitelist mail from Gmail, just add ".google.com" to the 
"whitelist" table, which is included in the supplied default
whitelist.

To install the default whitelist, make sure you have the proper
MySQL credentials and then issue the below command.

```
$ mysql gld <table-whitelist.sql
```

Whitelisting by DNS works on up to 5 levels of DNS "nodes", so
you can either do a very wide whitelisting of for example ".com"
or more specific whitelist of ".doodles.google.com".
