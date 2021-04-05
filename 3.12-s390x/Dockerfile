FROM s390x/alpine:3.12

ENV \
   # container/su-exec UID \
   EUID=1001 \
   # container/su-exec GID \
   EGID=1001 \
   # container/su-exec user name \
   EUSER=docker-user \
   # container/su-exec group name \
   EGROUP=docker-group \
   # container user home dir \
   EHOME= \
   # should user created/updated to use nologin shell? (yes/no) \
   ENOLOGIN=yes \
   # should user home dir get chown'ed? (yes/no) \
   ECHOWNHOME=no \
   # additional directories to create + chown (space separated) \
   ECHOWNDIRS= \
   # additional files to create + chown (space separated) \
   ECHOWNFILES= \
   # container timezone \
   TZ=UTC

# Install shadow (for usermod and groupmod) and su-exec
RUN \
   apk --no-cache --update add \
   shadow \
   su-exec \
   tzdata

COPY \
   chown-path \
   set-user-group-home \
   entrypoint-crond \
   entrypoint-exec \
   entrypoint-su-exec \
   /usr/bin/

RUN \
   chmod +x \
   /usr/bin/chown-path \
   /usr/bin/set-user-group-home \
   /usr/bin/entrypoint-crond \
   /usr/bin/entrypoint-exec \
   /usr/bin/entrypoint-su-exec
