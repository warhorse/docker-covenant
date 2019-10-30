# [warhorse/covenant](https://github.com/warhorse/docker-covenant)
[![GitHub Release](https://img.shields.io/github/release/war-horse/docker-covenant.svg?style=flat-square&color=E68523)](https://github.com/war-horse/docker-covenant/releases)
[![MicroBadger Layers](https://img.shields.io/microbadger/layers/warhorse/covenant.svg?style=flat-square&color=E68523)](https://microbadger.com/images/warhorse/covenant "Get your own version badge on microbadger.com")
[![MicroBadger Size](https://img.shields.io/microbadger/image-size/warhorse/covenant.svg?style=flat-square&color=E68523)](https://microbadger.com/images/warhorse/covenant "Get your own version badge on microbadger.com")
[![Docker Pulls](https://img.shields.io/docker/pulls/warhorse/covenant.svg?style=flat-square&color=E68523)](https://hub.docker.com/r/warhorse/covenant)
[![Docker Stars](https://img.shields.io/docker/stars/warhorse/covenant.svg?style=flat-square&color=E68523)](https://hub.docker.com/r/warhorse/covenant)

[Covenant](https://github.com/cobbr/Covenant) - A collaborative .NET C2 framework for red teamers.


![Covenant](https://raw.githubusercontent.com/wiki/cobbr/Covenant/covenant.png)

## Usage

Here are some example snippets to help you get started creating a container.

### docker

```
docker create \
  --name=covenant \
  -e TZ=Europe/London \
  -p 7443:7443 \
  -p 443:443 \
  -p 80:80 \
  -v <path to data>:/app/Data \
  --restart unless-stopped \
  warhorse/covenant
```

### docker-compose

Compatible with docker-compose v2 schemas.

```
---
version: "2"
services:
  covenant:
    image: warhorse/covenant
    container_name: covenant
    environment:
      - TZ=Europe/London
    volumes:
      - <path to data>:/app/Data
    ports:
      - 7443:7443
      - 443:443
      - 80:80
    restart: unless-stopped
```

## Parameters

Container images are configured using parameters passed at runtime (such as those above). These parameters are separated by a colon and indicate `<external>:<internal>` respectively. For example, `-p 8080:80` would expose port `80` from inside the container to be accessible from the host's IP on port `8080` outside the container.

| Parameter | Function |
| :----: | --- |
| `-p 7443` | The port for the Covenant Admin web interface |
| `-p 80` | The port for HTTP C2 traffic |
| `-p 443` | The port for HTTPS C2 traffic |
| `-e TZ=Europe/London` | Specify a timezone to use EG Europe/London|
| `-v /app/Data` | covenant configs |

&nbsp;
## Application Setup

Access the webui at `<your-ip>:7443`, for more information check out [Covenant](https://github.com/cobbr/Covenant).



## Support Info

* Shell access whilst the container is running: `docker exec -it covenant /bin/bash`
* To monitor the logs of the container in realtime: `docker logs -f covenant`

## Building locally

If you want to make local modifications to these images for development purposes or just to customize the logic:
```
git clone https://github.com/warhorse/docker-covenant.git
cd docker-covenant
docker build \
  --no-cache \
  --pull \
  -t warhorse/covenant:latest .
```
## Versions

* **10.30.19:** - First Push