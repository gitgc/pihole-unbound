## Installation
Instructions assume you have installed both Docker and Docker Compose.

### 1. Unbound
Get root hints, copy to ./unbound/root.hints, e.g.

`wget -O ./unbound/root.hints https://www.internic.net/domain/named.root`

This File must be present!

then:

`docker-compose up -d unbound`

#### Test
(if no `dig`, `apt install dnsutils`)

`dig www.google.com @172.20.0.7 -p 5053`

`dig www.google.com @127.0.0.1 -p 5053`

### 2. PiHole

`docker-compose up -d pihole`

#### Test

`dig www.google.com @172.20.0.6 -p 53`

`dig www.google.com @127.0.0.1 -p 53`

visit http://192.168.1.4/admin/index.php

## Commands to troubleshoot

`docker ps`

`docker inspect` <container name, such as pihole or unbound>

`docker logs pihole`

## Maintenance and Update

`docker pull pihole/pihole:latest`

`docker pull mvance/unbound-rpi:latest`

`docker stop pihole`

`docker stop unbound`

`docker rm pihole`

`docker rm unbound`

`docker-compose up -d unbound`

`docker-compose up -d pihole`