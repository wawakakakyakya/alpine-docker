FROM alp-edge:latest

# install package
RUN apk update \
    && apk --no-cache add rsyslog \
    && rc-update add rsyslog \
    && rm -rf /var/cache/apk/*

EXPOSE 514/udp

CMD ["/sbin/init"]
