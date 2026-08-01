# Vaultwarden

## Overview

- Vaultwarden is a self-hosted, community driven password manager.

## Purpose

- I included Vaultwarden in my home lab because I wanted to learn more about password managers, https,  and self-signed certificates. Also, I want to practice making backups and provide updates to the application.
 
## Role in my home lab

- Vaultwarden is the servers self-hosted password manager. It connects to the official Bitwarden application. Encryption, updates, and backups are the responsibility of the user. All storage of passwords will be on the server so strong security in very important.
   
## Installation

- Create directory for vaultwarden
- Create Docker compose file
- Create vaultwarden.env
- Create directory for caddy/data caddy/config

## Commands used

- mkdir vaultwarden
- cd vaultwarden
- sudo nano docker-compose.yml
- mkdir data
- sudo docker compose up -d
- mkdir -p caddy/data caddy/config
- sudo nano caddy/Caddyfile
- sudo nano vaultwarden.env

  ## Testing

  - I accessed vaultwarden via the browser on port 8083.
 
  <img width="1138" height="443" alt="Screenshot 2026-07-24 182452" src="https://github.com/user-attachments/assets/eaa608ae-8ac6-45a4-a010-660bb773deee" />

