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
- Immich has been installed in docker:

![Screenshot 2026-07-13 at 6 01 03 AM](https://github.com/user-attachments/assets/8c953d2c-5bdf-4c8c-9400-3cd4170e5906)


- Immich's dashboard has been accessed via a web browser:


<img width="1916" height="1013" alt="Screenshot 2026-07-13 061006" src="https://github.com/user-attachments/assets/86b6e9a2-3689-40e1-8e70-4e1a212ee529" />

## Troubleshooting
- This lab went smoothly without any issues

## Lessons Learned
- Immich creates 4 containers. immich_server, immich_machine_learning, immich_redis, & immich_postgres.
- Forwarding port 2283 directly to the internet without configuring a VPN tunnel is not secure. Doing this would risk being a victim of a man in the middle attack.
























![Screenshot 2026-07-13 at 6 01 03 AM](https://github.com/user-attachments/assets/51b6a1c7-b23a-4be8-8c31-7fba5639585b)
