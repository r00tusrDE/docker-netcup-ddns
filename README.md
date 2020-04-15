# docker-netcup-ddns

A netcup DynDNS client wrapped inside a Docker container.

### Built With
* [ownDynDNS](https://github.com/fernwerker/ownDynDNS/tree/7f6291964e4aca4c612c69dc7839077623bde1f2)
* [PHP](https://www.php.net)
* [NGINX](https://www.nginx.com)
* [Docker](https://www.docker.com)

## Prerequisites
* Install git via your package manager
```sh
# Ubuntu / Debian
$ sudo apt install git

# CentOS / Fedora
$ sudo yum install git

# Arch
$ sudo pacman -S git

# openSUSE
$ sudo zypper install git
```
* Install Docker and docker-compose
- Install Docker on [CentOS](https://docs.docker.com/engine/install/centos) | [Debian](https://docs.docker.com/engine/install/debian) | [Fedora](https://docs.docker.com/engine/install/fedora) | [Ubuntu](https://docs.docker.com/engine/install/ubuntu)
- Install [docker-compose](https://docs.docker.com/compose/install)

## Getting started
1. Clone this repo and its submodule
```sh
$ git clone --recurse-submodules https://github.com/r00tusrDE/docker-netcup-ddns
```
2. Edit the nginx vhost name and the HTTP port in docker-compose.yml
3. Start the Docker containers
```sh
$ docker-compose up -d
```

## Usage
For information on how to use the PHP script (ownDynDNS) take a look at their [README.md](https://github.com/fernwerker/ownDynDNS/blob/7f6291964e4aca4c612c69dc7839077623bde1f2/README.md).
Just skip the part that says "Copy all files to your webspace" and follow the rest of the installation how-to and you are good to go.

## License
Distributed under the MIT License. See `LICENSE` for more information.
