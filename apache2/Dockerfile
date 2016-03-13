FROM resin/raspberrypi3-buildpack-deps

ENV LANG C.UTF-8

RUN echo "deb http://archive.raspberrypi.org/debian/ jessie main ui staging" > /etc/apt/sources.list.d/raspi.list
RUN rm -f /usr/bin/entry.sh
RUN wget -qO - http://archive.raspberrypi.org/debian/raspberrypi.gpg.key | apt-key add -

RUN set -x && \
    apt-get update && \
    apt-get install apache2 php5 libapache2-mod-php5 php5-mysql ssl-cert php-pear openssl-blacklist -y && \
    rm -rf /var/lib/apt/lists/* 

VOLUME ["/var/www", "/var/log/apache2", "/etc/apache2", "/etc/ssl", "/etc/php5"]

COPY httpd-foreground /usr/bin/httpd-foreground

RUN chmod u+x /usr/bin/httpd-foreground

EXPOSE 80 443

ENTRYPOINT []
CMD ["httpd-foreground"]
