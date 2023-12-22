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
### Installation
* create a copy of `.env.dist` as `.env` and configure:
  * `username` -> The username for your Router to authenticate (so not everyone can update your DNS)
  * `password` -> password for your Router
  * `apiKey` -> API key which is generated in netcup CCP
  * `apiPassword` -> API password which is generated in netcup CCP
  * `customerId` -> your netcup Customer ID
  * `debug` -> true|false enables debug mode and generates output of update.php (normal operation has no output)
  
* Create each host record in your netcup CCP before using the script. The script does not create any missing records.

### AVM FRITZ!Box Settings
* Go to "Internet" -> "Freigaben" -> "DynDNS"
* Choose "Benutzerdefiniert"
* Update-URL: `https://<url of your webspace>/update.php?user=<username>&password=<pass>&ipv4=<ipaddr>&ipv6=<ip6addr>&domain=<domain>`
  * only the url needs to be adjusted, the rest is automatically filled by your AVM FRITZ!Box
  * http or https is possible if valid SSL certificate (e.g. Let's Encrypt)
* Domainname: `<host record that is supposed to be updated>`
* Username: `<username as defined in .env file>`
* Password: `<password as definied in .env file>`

For the original tutorial on how to use the PHP script (ownDynDNS) take a look at their [README.md](https://github.com/fernwerker/ownDynDNS/blob/7f6291964e4aca4c612c69dc7839077623bde1f2/README.md).

## run as cronjob on a **nix based device
* see [examples](./examples)

## References
* DNS API Documentation: https://ccp.netcup.net/run/webservice/servers/endpoint.php
* Source of dnsapi.php: https://ccp.netcup.net/run/webservice/servers/endpoint.php?PHPSOAPCLIENT

## License
The `ownDynDNS` submodule is distributed under the GPLv3 License. See [ownDynDNS/LICENSE](https://github.com/fernwerker/ownDynDNS/blob/7f6291964e4aca4c612c69dc7839077623bde1f2/LICENSE) for more information.
The rest of the project is distributed under the MIT License. See `LICENSE` for more information.
