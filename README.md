docker-devenv
=============

Create:
* PHP5.5 container with debian Wheezy
* Nginx container with Debian Wheezy 
* varnish container with Debian Wheezy 

# Usage
We will use [fig](http://www.fig.sh/) to start all our container in the good order.

## Installation
```sh
$(boot2docker shellinit)
curl -L https://github.com/docker/fig/releases/download/1.0.1/fig-`uname -s`-`uname -m` > /usr/local/bin/fig; chmod +x /usr/local/bin/fig
fig --version
```

## General Configuration
The database container is accessible with the name ```db```.  
The web site file must be put in the ```www``` folder on the host of the containers.

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
