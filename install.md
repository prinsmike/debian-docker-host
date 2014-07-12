Install
=======

* vim
    A useful text editor that should be installed on all host operating systems as well as all docker containers that allow interactivity.
* OpenSSH
    OpenSSH must be installed on all host operating systems. It is also useful if installed on interactive docker containers.
* Systemd
    Systemd should be used to manage docker as well as all docker containers on the host operating system. Systemd is not currently a good solution for running services inside containers; instead, supervisord should be used until there is a straightforward way to utilize Systemd inside docker containers. Take a look at the following links for more information:

    - https://github.com/dotcloud/docker/pull/5773
    - https://github.com/dotcloud/docker/issues/3629
    - http://rhatdan.wordpress.com/2014/04/30/running-systemd-within-a-docker-container/
    - http://lists.freedesktop.org/archives/systemd-devel/2014-May/018998.html