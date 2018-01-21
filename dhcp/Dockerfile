FROM alp-edge:latest

USER root

# install package
RUN apk update \
    && apk --no-cache add dhcp \
    && rc-update add dhcpd \
    && rm -rf /var/cache/apk/*

RUN touch /var/lib/dhcp/dhcpd.leases \
    && mkdir /tftpboot

COPY pxelinux.0 /tftpboot/pxelinux.0

EXPOSE 67/udp

CMD ["/sbin/init"]
