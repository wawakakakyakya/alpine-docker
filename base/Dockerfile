FROM alpine:edge
MAINTAINER wawakakakyakya

USER root

# add repositories
RUN echo -e "http://dl-4.alpinelinux.org/alpine/v3.5/community"  >> /etc/apk/repositories \
    && echo -e "http://dl-4.alpinelinux.org/alpine/edge/testing" >> /etc/apk/repositories
# echo "http://alpine.gliderlabs.com/alpine/edge/main"

# update package
RUN apk update \
    && apk upgrade \
    && apk --no-cache add openrc tzdata

# RUN apk --no-cache add vim net-tools openrc \
#     && apk --no-cache add --virtual=bash-dependencies bash bash-doc bash-completion

# https://blog.adachin.me/wordpress/archives/4177
# https://github.com/gliderlabs/docker-alpine/issues/183
# Install openrc, openrc is service manager.

# Tell openrc its running inside a container, till now that has meant LXC
RUN sed -i 's/#rc_sys=""/rc_sys="lxc"/g' /etc/rc.conf \
# Tell openrc loopback and net are already there, since docker handles the networking
    && echo 'rc_provide="loopback net"' >> /etc/rc.conf \
# no need for loggers
    && sed -i 's/^#\(rc_logger="YES"\)$/\1/' /etc/rc.conf \
# can't get ttys unless you run the container in privileged mode
    && sed -i '/tty/d' /etc/inittab \
# can't set hostname since docker sets it
    && sed -i 's/hostname $opts/# hostname $opts/g' /etc/init.d/hostname \
# can't mount tmpfs since not privileged
    && sed -i 's/mount -t tmpfs/# mount -t tmpfs/g' /lib/rc/sh/init.sh \
# can't do cgroups
    && sed -i 's/cgroup_add_service /# cgroup_add_service /g' /lib/rc/sh/openrc-run.sh \
    && rc-status \
    && touch /run/openrc/softlevel

# change TimeZone JST
RUN cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime \
    && apk del tzdata
