# Linux Server Administration Project
Download Ubuntu Server, ssh into it and use basic admin commands in it.

## Project Overview
I built an Ubuntu Server, connected to it using the SSH command, and performed basic system administration.

## Goal
- To learn by doing.
- To remotely manage a server from another computer's terminal.

## Lab Environment
- Host computer: Macbook & Windows PC
- Server OS: Ubuntu Server
- Virtualization tool: Virtualbox
- Network type: Bridged adapter
- Remote access: SSH

  ## Steps Performed

  ### Step 1: Installation of Ubuntu Server
  On a Windows PC I downloaded Virtualbox and I also downloaded the Ubuntu Server iso from the official Ubuntu website.
  I created a new machine on Virtualbox and completed the basic setup.
<img width="642" height="512" alt="Screenshot 2026-06-02 054500" src="https://github.com/user-attachments/assets/17174e9f-916b-4fe7-a635-25486e2ca731" />

### Step 2: Found the Server's IP address
Command used: ip a.

### Step 3: Installed SSH
Command: sudo apt update.
Command: sudo apt install openssh-server.
OpenSSH allows remote login access.          

### Step 4: Checked SSH Status
Command: sudo systemctl status ssh.
This command verifies whether the SSH service is running or not.
<img width="642" height="512" alt="Screenshot 2026-06-02 061818" src="https://github.com/user-attachments/assets/aae66e03-c79d-4e93-9ccf-16cbef1a0f13" />

### Step 5: Connected to the Server from another computer
Command: ssh username@server_ip_address
This command will connect a different computer to the server remotely using the SSH protocol.
![Screenshot 2026-06-03 at 6 06 23 AM](https://github.com/user-attachments/assets/b7b28f53-7311-41a9-b24d-a9a897ce45e1)

### Step 6: Basic Administration Commands Practiced
-Command to check the current user: who am i

-Command to check disk space: df -h

<img width="642" height="512" alt="Screenshot 2026-06-02 063300" src="https://github.com/user-attachments/assets/1aad7753-9e8f-42d2-81d9-f978117b9ae2" />

-Command to check memory usage: free -h

-Command to check running processes: ps aux

-Command to list files and directories: ls -la

## Troubleshooting
- I attempted to ssh into the ubuntu server but the connection refused.
- After researching this issue I learned that openssh needed to be installed.
- I installed openssh on the server and then I was able to ssh into the server from my macbook.
