FROM alpine:3.14.2

RUN apk add --no-cache apache2 && \
    mkdir -p /var/www/localhost/htdocs/OS && \
    mkdir -p /var/www/localhost/htdocs/kickstart


EXPOSE 80

WORKDIR /var/www

VOLUME /var/www/localhost/htdocs/OS
VOLUME /var/www/localhost/htdocs/kickstart
VOLUME /var/ww/logs

CMD  ["/usr/sbin/httpd", "-D", "FOREGROUND"]
