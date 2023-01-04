# Docker Setup - Homelab

## Contents

1. [Docker Installtion](#Docker-Installation)
2. [Docker-Compose-File anpassen](#anpassungen-in-der-compose-file-vornehmen)
<br>
<br>
---

## Docker Installation

<br>

Docker mit dem Schell-Script herunterladen:

````
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh
````

*[Quelle](https://github.com/docker/docker-install)*

<br>
<br>

---

## Auflistung der Services & Doku

* [Traefik Docker](https://hub.docker.com/_/traefik) | [Traefik Doku](https://doc.traefik.io/traefik/)
* [Dashy Docker](https://hub.docker.com/r/lissy93/dashy) | [Dashy Doku](https://github.com/Lissy93/dashy)
* [Portainer Docker](https://hub.docker.com/r/portainer/portainer) | [Portainer Doku](https://www.portainer.io/)
* [MySQL Docker](https://hub.docker.com/_/mysql)
* [phpMyAdmin Docker](https://hub.docker.com/_/phpmyadmin) | [phpMyAdmin Doku](https://docs.phpmyadmin.net/de/latest/)
* [NodeRed Docker](https://hub.docker.com/r/nodered/node-red) | [NodeRed Doku](https://nodered.org/docs/getting-started/docker)
* [Uptime-Kuma Docker](https://hub.docker.com/r/louislam/uptime-kuma) | [Uptime-Kuma Doku](https://uptime.kuma.pet/docs/)
* [Nextcloud Docker](https://hub.docker.com/_/nextcloud) | [Nextcloud Doku](https://docs.nextcloud.com/)
* [Grafana Docker](https://hub.docker.com/r/grafana/grafana) | [Grafana Doku](https://grafana.com/docs/grafana/v8.5/installation/docker/)
* [Photoprism Docker](https://hub.docker.com/r/photoprism/photoprism) | [Photoprism Doku](https://docs.photoprism.app/)

<br>
<br>

---
## Anpassungen in der Compose-File vornehmen

<br>

In der Docker-Compose-File die Anpassungen für die DNS-Namen und die Passwörter vornehmen.

````
vim docker-compose.yml
````
Zertifikate können durch die "Traefik Labels" von "production" auf "staging" geändert werden.
````
- "traefik.http.routers.grafana.tls.certresolver=production"
````
<br>
<br>

---
## Docker Compose auf Host ausführen

<br>

Den Ordner mit der Docker-Compose-File und den Konfiguartionen für die Apps auf den Ziel-Host kopieren. In dem Ordnern den folgenden Command ausführen.

````
docker compose up -d
````
<br>
<br>

---
## DNS Information
Um die Services über den DNS-Namen im Heimnetz nutzen zu könenn wird ein DNS-Server benötigt, ich nutze PiHole auf einem anderen Host (RaspberryPi), dort wurde für jeden Service ein A-Record gesetzt mit der IP-Adresse des Docker-Hosts.

*[PiHole Installation](https://docs.pi-hole.net/main/basic-install/)*
<br>
<br>

---
## Passwörter

<br>

Auflistung der Default-Logins:

* Grafana:
    * User: admin
    + Password: admin
