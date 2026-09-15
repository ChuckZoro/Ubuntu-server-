<img width="1064" height="65" alt="Screenshot 2026-09-13 133711" src="https://github.com/user-attachments/assets/11c4079e-1ab6-456b-92cd-e8ce7d57563a" />
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

## Troubleshooting

- After running sudo systemctl restart ssh I got this error:

<img width="1064" height="65" alt="Screenshot 2026-09-13 133711" src="https://github.com/user-attachments/assets/4a004882-0060-4263-9bf0-b9dd190ef634" />

- I tried to set password authentication to no in the /etc/ssh/sshd_config file but I was unsuccessful.
- /etc/ssh/sshd_config file states that /etc/ssh/sshd_config.d/*.conf takes precedence over the latter. I created that file an added:

PubkeyAuthentication yes

PasswordAuthentication no

KbdInteractiveAuthentication no

-This resolved my issue.


![Screenshot 2026-09-14 at 7 58 08 PM](https://github.com/user-attachments/assets/3d600327-37a2-4c16-ae9d-315ba4629836)
  


<img width="1064" height="65" alt="Screenshot 2026-09-13 133711" src="https://github.com/user-attachments/assets/4a004882-0060-4263-9bf0-b9dd190ef634" />


