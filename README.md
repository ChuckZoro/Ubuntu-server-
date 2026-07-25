# Linux Server Administration And Infrastructure Project

## Overview

This project documents the creation of my Docker-based home lab. It includes building network infrastructure and secure application hosting.

## Project Goals

- Learn by doing
- Apply skills from Network+
- Learn Docker and Docker Compose
- Build Infrastructure
- Host applications
- Secure services with https
- Practice troubleshooting and documentation

  ## Technologies Used

- Linux
- Docker
- Docker Compose
- Nginx
- Pi-hole
- Immich
- Filebrowser
- Vaultwarden
- Uptime Kuma

  ## Architecture

  - Docker runs the applications inside a container on my Linux Server.
  - Pi-hole provides DNS
  - Nginx creates a reverse proxy for better security
  - Immich provides cloud storage for photos
  - Filebrowser allows access to files in the cloud
  - Uptime Kuma provides network monitoring
  - Vaultwarden provides password manager sevices
 
    ### Infrastructure

    - [Docker](docs/Docker.md)
    - [Nginx](docs/Nginx & docker compose.md)
