# Nginx Proxy Manager

## Overview

- A reverse proxy is a server that sits in front of and conceals the identity of backend servers.

## Purpose

- I included a reverse proxy to this lab to increase security through HTTPS. To allow my proxy manager to communicate with the other containers it's necessary to create a shared network to resolve each container by name through the Nginx proxy manager.

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
