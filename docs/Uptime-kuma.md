# Uptime Kuma

## Overview

- Uptime Kuma is a monitoring tool that allows you to monitor different services such as HTTP/HTTPS websites, SSL certificates, TCP Ports, Apps, and MySQL databases.

## Purpose

- The purpose of adding Uptime Kuma to my project is to monitor all of my services in my server and to be notified when a service is down. I will set up notifications that will notify me using a chatbot via telegram.
 
## Installation

- Create a directory for Uptime Kuma
- Create docker compose file
- Run docker compose
   
## Commands used

- mkdir uptime-kuma
- cd uptime-kuma
- sudo nano docker-compose.yml
- sudo docker compose up -d

## Network Configuration

- Port 3001
- http://192.168.1.107:3001

## Testing

- I accessed Uptime Kuma from my browser. I enabled notifications to my filebrowser. I then removed the service from docker to see if I would receive a notification from telegram stating that a service was down.

   <img width="680" height="504" alt="Screenshot 2026-08-02 110942" src="https://github.com/user-attachments/assets/08b2977d-955a-4091-a712-b6fc02efa20f" />


   <img width="2509" height="1311" alt="Screenshot 2026-08-04 045555" src="https://github.com/user-attachments/assets/860531a1-4691-4a36-8834-7c15b064fbd5" />


   <img width="2513" height="1285" alt="Screenshot 2026-08-04 045917" src="https://github.com/user-attachments/assets/2507a4fe-16b9-4190-9a75-ffe9b5c2d53c" />

## Troubleshooting

- Vaultwarden service was showing down because Uptime Kuma did not recognize the self-signed certificate.

<img width="1675" height="1225" alt="Screenshot 2026-08-02 115807" src="https://github.com/user-attachments/assets/f5f856a0-93e4-440b-aa4c-ac348a55c08a" />





