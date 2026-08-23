# Nginx Proxy Manager

## Overview

- A reverse proxy is a server that sits in front of and conceals the identity of backend servers.

## Purpose

- I included a reverse proxy to this lab to increase security through HTTPS.

- To allow my proxy manager to communicate with the other containers it's necessary to create a shared network to resolve each container by name through the Nginx Proxy Manager.

## Installation

- Create a new docker network.

- Create a yaml file for Nginx proxy manager.

- Buy a domain.

- Obtain an Api Token.

- Create Proxy Hosts.

- Create HTTPS certificates.

- Create an A record for your domain.

## Commands Used

- sudo docker create proxy

- sudo docker compose up -d

- sudo docker network inspect proxy

- mkdir nginx

- cd nginx

- sudo nano docker-compose.yml

- sudo docker ps

## Testing

- docker network inspect showing all containers:

![Screenshot 2026-08-21 at 4 51 58 AM](https://github.com/user-attachments/assets/82760f0d-b2fe-434a-8cc5-a364e0bcf507)


![Screenshot 2026-08-21 at 4 51 29 AM](https://github.com/user-attachments/assets/c9df24f5-1132-42e2-8def-4d54966e58b0)


![Screenshot 2026-08-21 at 4 52 47 AM](https://github.com/user-attachments/assets/e141ead9-9b5b-4ba6-96a6-c9c0abeff34a)


- Nginx Proxy Manager proxy host list:


<img width="1950" height="622" alt="Screenshot 2026-08-23 042442" src="https://github.com/user-attachments/assets/6fd9cc9f-b3a1-45b9-8902-6a26a8aefaf2" />


Filebrowser loading over HTTPS:


<img width="3441" height="1628" alt="Screenshot 2026-08-23 031855" src="https://github.com/user-attachments/assets/0ec2c24f-f3e8-402f-be36-68eb5e8058de" />


## Troubleshooting

- Vaultwarden was interfering with starting the Nginx Proxy Manager:


![Screenshot 2026-08-13 at 4 59 06 AM](https://github.com/user-attachments/assets/54699692-5cb7-4f22-800c-6cbf7f4b044e)

- To resolve this issue I removed Caddy from the yaml file.

- Nginx Proxy Manager running:


<img width="1951" height="390" alt="Screenshot 2026-08-23 044443" src="https://github.com/user-attachments/assets/a0678811-36d8-441f-9934-68ca59f0ccfa" />


- I received a 502 Bad Gateway message:


<img width="427" height="175" alt="Screenshot 2026-08-23 023957" src="https://github.com/user-attachments/assets/b8f61774-eccf-4fb6-894d-d3ebc351f1ca" />

- To resolve this issue I changed the internal port in Nginx Proxy Manager from 8082 to port 80.

- File browser working with Nginx Proxy Manager properly configured:


<img width="3441" height="1628" alt="Screenshot 2026-08-23 031855" src="https://github.com/user-attachments/assets/16710a3d-4b95-4261-bdc4-86c0500eb1e3" />

## Lessons learned

- When you create your own domain you can set up DNS zones within that domain to point towards different services.

- When you put the proxy manager on a shared docker network you connect to them using internal port numbers.


