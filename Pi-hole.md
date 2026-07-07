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

  -Also, I received this error message as well:



  


  


