FROM alp-edge:latest

# install package
RUN apk update \
    && apk --no-cache add chrony dhcp \
    && rc-update add chronyd \
    && rc-update add dhcpd \
    && rm -rf /var/cache/apk/*

RUN touch /var/lib/dhcp/dhcpd.leases

EXPOSE 67/udp 123/udp 323/udp

CMD ["/sbin/init"]
