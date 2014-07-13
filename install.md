Install
=======

This file provides some suggestions for software to install on a Debian host installation.

* __vim__

    A useful text editor that should be installed on all host operating systems as well as all docker containers that allow interactivity.

* __sudo__

    Sudo allows us to create a user with root privileges, while password protecting root privileges.

* __OpenSSH__

    OpenSSH must be installed on all host operating systems. It is also useful if installed on interactive docker containers.

* __Systemd__

    Systemd should be used to manage docker as well as all docker containers on the host operating system. Systemd is not currently a good solution for running services inside containers; instead, supervisord should be used until there is a straightforward way to utilize Systemd inside docker containers. Take a look at the following links for more information:

    - https://github.com/dotcloud/docker/pull/5773
    - https://github.com/dotcloud/docker/issues/3629
    - http://rhatdan.wordpress.com/2014/04/30/running-systemd-within-a-docker-container/
    - http://lists.freedesktop.org/archives/systemd-devel/2014-May/018998.html

* __Git__

    Install Git to clone this repository and easily gain access to the included files, such as docker.service, a Systemd file to run Docker.
