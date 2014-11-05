docker-devenv
=============

Docker Varnish - Nginx - PHP-FPM  
created from http://blog.nicolargo.com/2014/10/infra-lemp-docker.html

# Usage
We will use [fig](http://www.fig.sh/) to start all our container in the good order.

## Installation
```sh
$(boot2docker shellinit)
curl -L https://github.com/docker/fig/releases/download/1.0.1/fig-`uname -s`-`uname -m` > /usr/local/bin/fig; chmod +x /usr/local/bin/fig
fig --version
```

## Commands
__Start__
```sh
fig up -d
````

__Check state__
```sh
fig ps
```

__See container logs__
```sh
fig logs
````

__Stop__
```sh
fig stop
```

__Stop and remove__
```sh
fig stop && fig rm
```
