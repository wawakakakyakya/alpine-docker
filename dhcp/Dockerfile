FROM alp-edge:latest

# install package
RUN apk update \
    && apk --no-cache add dhcp \
    && rc-update add dhcpd \
    && rm -rf /var/cache/apk/*

RUN touch /var/lib/dhcp/dhcpd.leases

EXPOSE 67/udp

CMD ["/sbin/init"]
