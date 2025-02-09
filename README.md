# Overview

Docker images for running Ubiquiti's [UniFi Controller software](https://www.ubnt.com/download/unifi/) on a [Raspberry Pi](https://www.raspberrypi.org/).

# Supported tags and respective `Dockerfile` directory links

- [`6.1.71`, `6.1` (*v6.1.71/6.1*)](https://github.com/ryansch/docker-unifi-rpi/blob/v6.1.71/6.1)
- [`6.2.26`, `6.2` (*v6.2.26/6.2*)](https://github.com/ryansch/docker-unifi-rpi/blob/v6.2.26/6.2)
- [`6.4.54`, `6.4`, `6`, `latest` (*v6.4.54/6.4*)](https://github.com/ryansch/docker-unifi-rpi/blob/v6.4.54/6.4)
- [`6.5.42` (*6.5*)](https://github.com/ryansch/docker-unifi-rpi/blob/main/6.5)

## Versions
Ubiquiti releases 'unstable', 'testing', and 'stable candidate' versions as part of its beta group release structure.  These releases are included here.  Only stable releases are tagged with their general version (ex: `5.6` for the `5.6.30` stable release) or with `latest`.

## Supported Architectures
`arm32v7`,`arm64v8`, `amd64`

# Usage

## Prerequisites

A Raspberry Pi running with [Docker and Docker Compose installed](https://docs.docker.com/engine/installation/linux/docker-ce/debian/#install-using-the-convenience-script) on it. Guides such as [this](https://blog.alexellis.io/getting-started-with-docker-on-raspberry-pi/) or [this](https://blog.hypriot.com/getting-started-with-docker-and-mac-on-the-raspberry-pi/) are available for beginners.

## On rpi:

1. `mkdir unifi && cd unifi`
2. `curl -O https://raw.githubusercontent.com/ryansch/docker-unifi-rpi/main/docker-compose.yml`
3. (Optional) Edit `docker-compose.yml` to point to a different tag if you don't want `latest`.
4. `sudo docker-compose up -d`
5. If using [host networking](https://docs.docker.com/network/host/), you may need to open the appropriate firewall ports on your Docker host (e.g., `8080/tcp 8443/tcp 8843/tcp 8880/tcp 3478/udp`) before you can access the web interface.

## From any computer on your network:

Visit https://raspberrypi.local:8443/ with your browser. Replace `raspberrypi.local` with the actual hostname or local network IP address of your Raspberry Pi.

# Building
- `./build.sh -v <docker version> -u <unifi version> [-t <additional docker tag> ...]`

Example: `./build.sh -v 5.9.29 -u 5.9.29-04b5d20997 -t 5.9 -t 5 -t latest`

# Publishing
- `./publish.sh -v <docker version> -u <unifi version>`

Example: `./publish.sh -v 5.9.29 -u 5.9.29-04b5d20997`

# Tagging a stable release
- `./tag.sh -v <docker version> -u <unifi version> [-t <additional docker tag> ...]`

Example: `./tag.sh -v 5.9.29 -u 5.9.29-04b5d20997 -t 5.9 -t 5 -t latest`


# TLS Support
[TLS with Traefik](https://github.com/ryansch/docker-unifi-rpi/wiki/TLS-with-Traefik)
