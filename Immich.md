# Objective
- The objective of this lab is to install Immich into docker with docker compose and access the interface from a browser.

## Environment
- Windows PC
- Macbook
- Ubuntu server 26.04
- Apple Terminal

## Skills
- Docker compose
- Volume mapping
- Linux permissions
- Port mapping

## Implementation
- Create directory for Immich
- Create yaml file
- Create .env file
- Update timezone in .env file
- Make a new directory for uploaded files and one for your database files
- Access Immich interface via the web browser

## Commands used
- mkdir ./immich-app
- wget -O docker-compose.yml https://github.com/immich-app/immich/releases/latest/download/docker-compose.yml
- wget -O .env https://github.com/immich-app/immich/releases/latest/download/example.env
- mkdir -p library postgres
- sudo docker compose up -d
- http://192.168.1.107:2883

## Verification
- Immich installed in docker:
