# martinussuherman/alpine

---

## What is this image for ?

This is an [Alpine Linux](https://hub.docker.com/_/alpine/) or [Minimal Alpine Linux image with glibc](https://hub.docker.com/r/jeanblanchard/alpine-glibc) based image that bundles **tzdata**, **su-exec**, and some useful entrypoint scripts.

---

* [set-user-group-home](https://github.com/martinussuherman/alpine/blob/master/set-user-group-home)

  Creates/updates **user** with **userid**, **group**, **groupid** and **home** directory.
  The group and the home directory are assigned to the user, with **shell** set based on values of environment variable ```ENOLOGIN``` (see below for more info).

  User created/updated from environment variable ```EUSER``` (default ```docker-user```), with uid from environment variable ```EUID``` (default ```1001```).

  Group created/updated from environment variable ```EGROUP``` (default ```docker-group```), with gid from environment variable ```EGID``` (default ```1001```).

  Home directory created/updated from environment variable ```EHOME``` (default ```/home/docker-user```).

  If variable ```ENOLOGIN``` equals yes then use ```/sbin/nologin``` as **shell**, else use **default shell** (```/bin/sh```).

  If variable ```ECHOWNHOME``` equals yes then the home directory will be chown'ed to ```EUSER```:```EGROUP```

---

* [chown-path](https://github.com/martinussuherman/alpine/blob/master/chown-path)

  Chown directories in ```ECHOWNDIRS```, create them if not exist.
  Chown files in ```ECHOWNFILES```, create them if not exist.

---

* [entrypoint-su-exec](https://github.com/martinussuherman/alpine/blob/master/entrypoint-su-exec)
[command] [params...]

  First creates/updates user, group and home directory, by executing **```set-user-group-home```**.
  Then uses **```su-exec```** to exec ```$ENTRYPOINT_COMMAND``` with the given parameters as the user ```$EUSER```.

---

* [entrypoint-exec](https://github.com/martinussuherman/alpine/blob/master/entrypoint-exec)
[command] [params...]

  First creates/updates user, group and home directory, by executing **```set-user-group-home```**.
  Then uses **```exec```** to exec ```$ENTRYPOINT_COMMAND``` with the given parameters (as ```root```).

---

* [entrypoint-crond](https://github.com/martinussuherman/alpine/blob/master/entrypoint-crond) [params...]

  First creates/updates user, group and home directory, by executing **```set-user-group-home```**.
  Then sets the crontab file ```$CROND_CRONTAB``` as the crontab of the user ```$EUSER```.
  Finally executes **```crond```** with the given parameters.

---
