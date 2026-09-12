# Remote Access

## Overview
- This lab is about creating remote access to my server outside of my own network.
- For security there will be no open ports on my firewall.
- My server will connect to cloudflare via a outgoing connection which will prevent everything being exposed on my network.

## Network And Service Architecture

<img width="2007" height="1668" alt="mermaid-diagram" src="https://github.com/user-attachments/assets/ce3ede43-4fb6-4f11-9d61-6ad49e331079" />

- Pi-hole, File Browser, Immich, & Vaultwarden do not leave the internal network. Only Uptime-Kuma can be accessed from the internet.

## Cloudflared Yaml File

tunnel: <TUNNEL-UUID>
credentials-file: /home/vboxuser/.cloudflared/<TUNNEL-UUID>.json

ingress:
  - hostname: uptime-one.<Domain name>
    service: http://localhost:80
  - service: http_status:404

It's worth noting that the path has to be exact and the http status:404 has to be included or it will not work.

