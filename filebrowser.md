# Objective
- The objective of this lab is to install a filebrowser on docker and to access it from a browser.

## Skills
- Linux
- Docker Compose
- Docker images
- Yaml
- Port mapping

  ## Environment
- Windows PC
- Macbook
- Ios terminal
- Ubuntu server
- Virtual box VM

## Implementation
- Pull filebrowser image
- Create filebrowser directory
- Create Yaml file
- Acess file browser dashboard through the browser

  ## Commands used
- mkdir filebrowser
- nano compose.yml
- sudo docker pull filebrowser/filebrowser
- sudo docker compose up -d

  ## Verification
- Filebrowser installed in docker:

  ![Screenshot 2026-07-08 at 5 26 08 AM](https://github.com/user-attachments/assets/3e8b7c26-4226-4b63-9fb6-efc9cf4c2d4b)

  - Filebrowser accessed through the dashboard via the browser:
  

   <img width="1917" height="1044" alt="Screenshot 2026-07-08 061438" src="https://github.com/user-attachments/assets/8296abbc-345f-4b59-9f26-aaca3b1b9f80" />

   ## Troubleshooting
- I received this error message:

  ![Screenshot 2026-07-08 at 5 11 41 AM](https://github.com/user-attachments/assets/7fc23a7d-ff34-4151-9f34-1c3b3b0315b3)

  * This error message stated that there was a temporary failure resloving download.docker.com and other domain names. This is a DNS problem.
  * The problem was that Pi-hole (which is my DNS server now) was down.
  * To resolve this problem I changed directory into the pihole directory and ran sudo docker compose up -d.


- I also received this error:  
  
  




  


