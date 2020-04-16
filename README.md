# docker-netcup-ddns

Self-hosted dynamic DNS php script for FRITZ!Box and netcup DNS API wrapped inside Docker containers.

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
3. Change owner of the ownDynDNS folder recursive to the webserver user www-data
```sh
$ chown -R www-data:www-data ./ownDynDNS
```
4. Start the Docker containers
```sh
$ docker-compose up -d
```

## Usage
For information on how to use the PHP script (ownDynDNS) take a look at their [README.md](https://github.com/fernwerker/ownDynDNS/blob/7f6291964e4aca4c612c69dc7839077623bde1f2/README.md).
Just skip the part that says "Copy all files to your webspace" and follow the rest of the installation how-to and you are good to go.

## License
The `ownDynDNS` submodule is distributed under the GPLv3 License. See [ownDynDNS/LICENSE](https://github.com/fernwerker/ownDynDNS/blob/7f6291964e4aca4c612c69dc7839077623bde1f2/LICENSE) for more information.
The rest of the project is distributed under the MIT License. See `LICENSE` for more information.
