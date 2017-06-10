FROM alpine:latest

# ensure www-data user exists
RUN set -x && \
    addgroup -g 82 -S opensrf && \
    adduser -u 82  -D -S -G opensrf opensrf && \
    apk add --update wget gzip curl vim && \
    apk add --update make autoconf gcc && \
    cd /tmp && \
    curl https://evergreen-ils.org/downloads/opensrf-2.5.0.tar.gz -o opensrf.tar.gz && \
    tar -xvf opensrf.tar.gz && \
    cd opensrf-2.5.0 && \
    make -f src/extra/Makefile.install linux


# Install apache httpd
RUN apk add --update apache2  && \
    rm -rf /var/cache/apk/* && \
    mkdir -p /run/apache2

# Add the files
#ADD root /

#COPY files/httpd.conf /etc/apache2/.

# EntryPoint
ENTRYPOINT ["/init"]

CMD []

# Expose the ports for nginx
EXPOSE 22 80
