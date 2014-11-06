FROM debian:wheezy
MAINTAINER Guillaume PARIS <email>

ENV DEBIAN_FRONTEND noninteractive


# Update the package repository and install applications
RUN apt-get update && \
  apt-get upgrade -y && \
  apt-get -y install curl && \
  apt-get -y clean

RUN set -e; \
    curl http://repo.varnish-cache.org/debian/GPG-key.txt | apt-key add -; \
    echo "deb http://repo.varnish-cache.org/debian/ wheezy varnish-4.0 > /etc/apt/sources.list.d/varnish.list" \
    apt-get update && \
    apt-get install -y varnish;

# Make our custom VCLs available on the container
ADD default.vcl /etc/varnish/default.vcl

ENV VARNISH_BACKEND_PORT 80
ENV VARNISH_BACKEND_IP 172.17.42.1
ENV VARNISH_PORT 80

# Expose port 80
EXPOSE 80

ADD start.sh /start.sh
CMD ["/start.sh"]