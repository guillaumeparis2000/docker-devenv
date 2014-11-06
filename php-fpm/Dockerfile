FROM debian:wheezy
MAINTAINER Guillaume PARIS <email>

ENV DEBIAN_FRONTEND noninteractive

ADD http://http.debian.net/debian/project/trace/ftp-master.debian.org /etc/trace_ftp-master.debian.org
ADD http://security.debian.org/project/trace/security-master.debian.org /etc/trace_security-master.debian.org
ADD http://www.dotdeb.org/dotdeb.gpg /etc/apt/dotdeb.gpg

RUN echo 'deb http://packages.dotdeb.org wheezy all' > /etc/apt/sources.list.d/dotdeb.list && \
    echo 'deb http://packages.dotdeb.org wheezy-php55 all' > /etc/apt/sources.list.d/dotdeb-php5.list && \
    apt-key add /etc/apt/dotdeb.gpg && \
    rm /etc/apt/dotdeb.gpg

RUN apt-get update && \
    apt-get -y dist-upgrade

RUN apt-get -y install php5 php5-fpm php5-gd php5-ldap \
    php5-sqlite php5-pgsql php-pear php5-mysql \
    php5-mcrypt php5-xcache php5-xmlrpc

RUN sed -i '/daemonize /c \
daemonize = no' /etc/php5/fpm/php-fpm.conf

RUN sed -i '/^listen /c \
listen = 0.0.0.0:9000' /etc/php5/fpm/pool.d/www.conf

RUN sed -i 's/^listen.allowed_clients/;listen.allowed_clients/' /etc/php5/fpm/pool.d/www.conf

RUN mkdir -p /srv/http && \
    echo "<?php phpinfo(); ?>" > /srv/http/index.php && \
    chown -R www-data:www-data /srv/http

EXPOSE 9000
VOLUME /srv/http
ENTRYPOINT ["php5-fpm"]
