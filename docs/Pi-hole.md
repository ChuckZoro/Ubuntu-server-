## Objective
- The objective of this lab is to build on to the Ubutu server by installing Pi-hole and accessing the dashboard through the browser.

## Lab environment
- Ubuntu server 26.04

- Docker compose

- Docker

- Macbook & Windows PC

- Mac os terminal

- Pi-hole

  ## Skills

  - Administration
 
  - Networking
 
  - DNS
 
  - DHCP
 
  - Docker
 
  - Troubleshooting
  
## Implementation

- Pull Pi-hole image

- Write yaml file

- Use Docker compose to start Pi-hole

- Access the dashboard for Pi-hole through the browser

  ## Commands used

  - sudo docker pull pihole/pihole
 
  - mkdir pihole
 
  - nano compose yml
 
 ## Verification

 - Ran Pi-hole in docker:


![Screenshot 2026-07-06 at 5 42 52 AM](https://github.com/user-attachments/assets/ba1ce102-5f8a-40a2-871e-a5fc7e5c1ddf)

- Accessed Pi-hole via my browser:

 <img width="1920" height="1044" alt="Screenshot 2026-07-04 145357" src="https://github.com/user-attachments/assets/a04137a7-8e11-4106-a6e1-cf530711425a" />



## Troubleshooting

- I received this error message:


![Screenshot 2026-07-04 at 2 22 06 PM](https://github.com/user-attachments/assets/c6e6f2af-5de1-48a1-84a8-402c72095be1)

* There was a problem with Pi-hole being able to use port 53 because it was already in use. I ran the command "sudo ss -tulnp | grep" and determined that systemd-resolved was using port 53.
* To fix this issue I ran "sudo systemctl disable systemd-resolved" and "sudo systemctl stop systemd-resolved".

  - DNS resolution is currently unavailable:
  
  
    ![Screenshot 2026-07-04 at 2 30 07 PM](https://github.com/user-attachments/assets/d6d27207-628b-49e2-a0e7-de8b08c708f0)

* To resolve this issue I added the DNS information to the yaml file.

## Lessons learned

- In order to start Pi-hole I need to be in the pihole directory where the yaml file is stored.

- Putting different services in different directories protects against all services going down at once.

- Only one service can be listening on one IP address, port, and protocol at the same time, otherwise it will create a conflict.

- For pi-hole, DNS needs to be in the yaml file to operate.
  
- Pi-hole sits between your computer and the DNS resolver. It has the ability to block traffic at the DNS level, depending on if the domain name is on it's block list or not.

  


