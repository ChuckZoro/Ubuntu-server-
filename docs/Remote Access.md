# Remote Access

## Overview
- This lab is about creating remote access to my server outside of my own network.
- For security there will be no open ports on my firewall.
- My server will connect to cloudflare via a outgoing connection which will prevent everything being exposed on my network.

## Network And Service Architecture

<img width="2007" height="1668" alt="mermaid-diagram" src="https://github.com/user-attachments/assets/ce3ede43-4fb6-4f11-9d61-6ad49e331079" />

- Pi-hole, File Browser, Immich, & Vaultwarden do not leave the internal network. Only Uptime-Kuma can be accessed from the internet.

- VM: The machine hosting the software.

- cloudflared: The software that maintains the tunnel.

## Installed Cloudflared Apt Repository

sudo mkdir -p --mode=0755 /usr/share/keyrings
curl -fsSL https://pkg.cloudflare.com/cloudflare-main.gpg | sudo tee /usr/share/keyrings/cloudflare-main.gpg >/dev/null
echo 'deb [signed-by=/usr/share/keyrings/cloudflare-main.gpg] https://pkg.cloudflare.com/cloudflared any main' | sudo tee /etc/apt/sources.list.d/cloudflared.list
sudo apt update && sudo apt install cloudflared

- Package manager: Installs and updates that software.

## Cloudflared Yaml File

tunnel: <TUNNEL-UUID>
credentials-file: /home/vboxuser/.cloudflared/<TUNNEL-UUID>.json

ingress:
  - hostname: uptime-one.<Domain name>
    service: http://localhost:80
  - service: http_status:404

It's worth noting that the path has to be exact and the http status:404 has to be included or it will not work.

## Important Commands

- cloudflared tunnel login

- cloudflared tunnel create labs

- sudo mkdir -p /etc/cloudflared

## Images

<img width="1160" height="96" alt="Screenshot 2026-09-09 120824" src="https://github.com/user-attachments/assets/d86fc441-3ecb-45b0-b568-0821ca808c6a" />

- Cloudflared Tunnel Running.

<img width="1195" height="32" alt="Screenshot 2026-09-12 095647" src="https://github.com/user-attachments/assets/ac24ff02-9617-4053-8576-6ce54e4a6655" />

- Dns record that I created to point towards the cloudflared tunnel. Domain name has been edited out.

  <img width="871" height="233" alt="Screenshot 2026-09-09 160330" src="https://github.com/user-attachments/assets/49f89512-0e50-4903-8b07-ee5534190318" />

- I accessed Uptime-kuma vai cloudflared tunnel.

  ## Troubleshooting

  


## Troubleshooting



