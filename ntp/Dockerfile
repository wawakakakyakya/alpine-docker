FROM alp-edge:latest

# install package
RUN apk update \
    && apk --no-cache add chrony \
    && rc-update add chronyd \
    && rm -rf /var/cache/apk/*

EXPOSE 123/udp 323/udp

CMD ["/sbin/init"]
