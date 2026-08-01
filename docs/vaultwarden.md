# Vaultwarden

## Overview

- Vaultwarden is a self-hosted, community driven password manager.

## Purpose

- I included Vaultwarden in my home lab because I wanted to learn more about password managers, https,  and self-signed certificates. Also, I wanted to practice making backups and provide updates to the application.
 
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
 


  <img width="1886" height="1010" alt="Screenshot 2026-07-20 060720" src="https://github.com/user-attachments/assets/387ade9b-aa20-4229-a6fe-f14ad3c096e9" />

## Troubleshooting

- When I accessed the Vaultwarden dashboard I got a message that said that HTTPS is required.
- I needed to figure out how to encrypt the data going to vaultwarden.
- To accomplish this I used a self-signed certificate via caddy.
- In order to access the dashboard I added the hostname to the host file on Windows. C:\Windows\System32\drivers\etc\hosts  



<img width="1138" height="443" alt="Screenshot 2026-07-24 182452" src="https://github.com/user-attachments/assets/3966f537-aeb5-42af-a4c1-3c633d5dc6e4" />

## Lesson Learned

- Caddy has an internal CA that signs the certificate.
- Even though Caddy created a self-signed certificate my computer did not trust it. You can see why having a trusted third-party signed certificate is very important for security.
  
