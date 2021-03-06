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

Docker User
-----------

I like to set up a separate docker user to work with docker containers and volumes. The docker user is given sudo privileges so it can be used to manage docker containers. The docker user's home directory is created in /var, where shared docker volumes can be managed.

The user can be created with the following command:

```
useradd -m -g docker -s /bin/bash -d /var/docker docker
```

Make sure to give the user a strong password since the docker group is root-equivalent. See the following link for more details:

http://docs.docker.io.s3-website-us-west-2.amazonaws.com/articles/security/#dockersecurity-daemon

Modify the sudoers file, using `visudo`, and add the following line to give the dockeru user all sudo privileges:

```
docker ALL=(ALL) ALL
```

To make things a little easier on ourselves, we can extend the password timeout for sudo by adding the following line to our sudoers file:

```
Defaults timestamp_timeout=20
```

The time is given in minutes.

HAProxy
-------

In order to run multiple services on the same port on the host machine, it might be necessary to redirect traffic on that port to the correct service using a reverse proxy. A good choice, that also supports load balancing, is HAProxy. There is a trusted HAProxy container available on the official docker registry at https://registry.hub.docker.com/u/dockerfile/haproxy/.
