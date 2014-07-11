debian-docker-host
==================

Setting up a Debian based host for serving Docker containers.

Partitions
----------

* /boot (500M)
* swap (Memory size)
* / (8G)
* /var (Remainder of drive)

Systemd
-------

See the documentation at https://wiki.debian.org/systemd to install and enable systemd on Debian.

Other links that might be of interest:

* http://coreos.com/docs/launching-containers/launching/getting-started-with-systemd/
* https://docs.docker.com/articles/host_integration/
* http://www.freedesktop.org/wiki/Software/systemd/

Docker
------

Follow the instructions at https://scottlinux.com/2014/05/04/how-to-install-and-run-docker-on-debian-wheezy/ to setup Docker on Debian.
