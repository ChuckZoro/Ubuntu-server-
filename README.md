# Linux Server Administration Project
Download Ubuntu Server, SSh into it and use basic admin commands in it.

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
