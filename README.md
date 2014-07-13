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

### docker.service

Included in this repository, is a docker.service file that can be used to enable docker with Systemd. Copy the docker.service file to /lib/systemd/system/ and enable it with `systemctl enable docker.service`

### Start docker containers with Systemd

You can manage your docker containers with Systemd. This will allow you to start, stop and reload containers easily. Systemd can also restart your containers automatically whenever they fail. Look at the following resources for more information:

* https://docs.docker.com/articles/host_integration/
* http://coreos.com/docs/launching-containers/launching/getting-started-with-systemd/

HAProxy
-------

In order to run multiple services on the same port on the host machine, it might be necessary to redirect traffic on that port to the correct service using a reverse proxy. A good choice, that also supports load balancing, is HAProxy. There is a trusted HAProxy container available on the official docker registry at https://registry.hub.docker.com/u/dockerfile/haproxy/.
