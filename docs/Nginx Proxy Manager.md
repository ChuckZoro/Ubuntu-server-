# Nginx Proxy Manager

## Overview

- A reverse proxy is a server that sits in front and conceals the identity of backend servers.

## Purpose

- I included adding a reverse proxy to this lab to increase security through HTTPS and to create a shared network for all docker applications so I can access them by name in my browser.

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

