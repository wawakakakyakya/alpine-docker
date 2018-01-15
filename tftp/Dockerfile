FROM alp-edge:latest

# install package
RUN apk update \
    && apk --no-cache add tftp-hpa \
    && rc-update add in.tftpd \
    && rm -rf /var/cache/apk/*

EXPOSE 69/udp

CMD ["/sbin/init"]
