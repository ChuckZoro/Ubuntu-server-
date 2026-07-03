# Docker

## I will be installing Docker onto the Ubuntu server 

## Objective

- The objective of this project is to learn by doing and to document the lab clearly, troubleshoot the issues that I had, and to document the lessons that I learned from this lab.

## Skills
-Linux
-Docker
-Docker compose

## Lab environment
- HP All-In-One
  * Processor 11th Gen Intel Core i3
  * Memory 8 GB
  * Storage 477 GB

- Ubuntu server
  *26.04
  * Bridged adapter
  * Memory 4819 MB
  * Storage 25 GB

-MacBookAir 
  * macOS Sequoia
  * Memory 16 GB
  * Chip Apple M3

## Project Reqirements
- Ubuntu server 26.04 installed on a VM

## Implementation

1. Update the operating system
2. Add Docker's official GPG key
3. Add the repository to Apt sources
4. Install from Apt repository
5. Install docker

## Commands used

-Update operating system:
                          sudo apt update


-Add dockers official GPG key: 
                              
                               sudo apt install ca-certificates curl
                               
                               sudo install -m 0755 -d /etc/apt/keyrings
                               
                               sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
                               
                               sudo chmod a+r /etc/apt/keyrings/docker.asc

-Add the repository to Apt sources: 
                                   
                                    sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
                                    
                                    Types: deb
                                    
                                    URIs:https://download.docker.com/linux/ubuntu
                                    
                                    Suites:$(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
                                    
                                    Components: stable
                                    
                                    Architectures: $(dpkg --print-architecture)
                                    
                                    Signed-By: /etc/apt/keyrings/docker.asc
                                    
                                    EOF

                                    sudo apt update

-Install docker:

                 sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

-Verify that docker is running: 
                                
                                sudo systemctl status docker
                                
                                sudo docker run hello-world

## Troubleshooting
- While attempting to set up docker's apt repository I received this message:

   Error: Release file for http://us.archive.ubuntu.com/ubuntu/dists/resolute-updates/Inrelease is not valid yet (invalid for another 2d 15h 17min 24s) Updates for this repository will not be applied.

  * It seems that linux believed that the date was in the past. An adjustment was necessary. To resolve this issue I synchronized the time by running this command: sudo apt install systemd-timesyncd. To enable it I ran this command: sudo systemctl enable --now systemd-timesyncd

![Troubleshoot installing systemd-timesyncd](https://github.com/user-attachments/assets/e081054a-ebcc-46f0-9b15-985cb4ac313c)


## Verification

Status of docker:

![Screenshot 2026-07-02 at 6 30 47 AM](https://github.com/user-attachments/assets/adc57269-6383-4473-8193-da30bc0986a5)


Run hello-world in docker:

![Screenshot 2026-07-02 at 6 27 27 AM](https://github.com/user-attachments/assets/a6fa7e1f-c6a8-4e67-9a98-87d4e99e0d7a)

## Lessons learned

- I learned how to use the official documentation when learning about and installing a new technology.
- If your computer's clock is not sychronized with the Network Time Protocol there may be a valid certificate conflict.
- In github when adding a file to a repository, you need to add .md to the file to make it a markdown file. If not,  you will not be able to add photos to the file.





