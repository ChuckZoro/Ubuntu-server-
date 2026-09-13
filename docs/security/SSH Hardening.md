# Basic  SSH Hardening

## Overview

- In this lab I will improve the security of my server through ssh hardening which will require a public and private key to log in.

## Objectives

- Require SSH keys for authentication.
- Disable logging in via passwords to the server through ssh.
- Confirm that I can access the server via ssh keys from my remote computer.
  
## Why is this  lab important?

- Without this protection anyone could attempt to guess my password and possibly gain access.
- Having the private key is another factor of authentication but it needs to be protected.

## Commands used

- ssh-keygen -t ed25519
- ssh-copy-id vboxuser<ip of server>
- ssh vboxuser@<ip of server>
- sudo nano /etc/ssh/sshd_config
  Set: PasswordAuthentication no
  Set: PermitRootLogin no
- sudo systemctl restart ssh




