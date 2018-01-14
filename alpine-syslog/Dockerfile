FROM alp-edge:latest

# install package
RUN apk update \
    && apk --no-cache add rsyslog \
    && rc-update add rsyslogd \
    && rm -rf /var/cache/apk/*

EXPOSE 514/udp

CMD ["/sbin/init"]
