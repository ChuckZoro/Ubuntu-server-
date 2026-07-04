# Objective
- The objective of this lab is to install docker compose and nginx onto the ubuntu server and to access nginx from my browser.

## Skills

-Linux

-Docker compose

-Nginx

## Lab environment
- Host computer: Macbook $ Windows PC

- Hypervisor: Virtualbox

- Linux server 26.04 VM

- Docker

- Mac os terminal

- Nginx

## Project Requirements
- All of the previous labs in this repository.

  ## Implementation
  - Install docker compose from the repository
 
  - Pull nginx image
 
  - Run nginx
 
  - Access nginx from the browser

## Commands used

- sudo apt-get update

- sudo apt-get install docker-compose-plugin

- docker compose version

- sudo docker pull nginx:stable

- sudo docker run --name -d -p 8080:80 nginx:stable

- mkdir Docker

- mkdir nginx

- mkdir -p html

- nano compose.yaml

  ## Verification

  - Docker compose installed

![Screenshot 2026-07-04 at 10 58 59 AM](https://github.com/user-attachments/assets/689f1f6a-e2d5-409c-9a7a-4031f3bc8ab6)

Access nginx from my browser:

![Screenshot 2026-07-04 at 11 12 40 AM](https://github.com/user-attachments/assets/558305f4-7910-4b07-b412-cdf8a7c36ba7)

## Troubleshooting

- I had difficulty setting up volumes and the yaml file for docker compose. I created the yaml file but I ran into great difficulty with learning how to apply the code to the yaml file. As of now, I have not resolved this issue but I will continue to work on this issue.

  ## Lessons learned

- Docker compose simplifies running and stopping a container.  It requires a yaml file.

- Nginx web server can be accessed anywhere from the internet and also can be configures as a reverse proxy
  


