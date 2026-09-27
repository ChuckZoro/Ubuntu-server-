# User account for claude

## Overview

- The point of this lab is to create an account so claude can access my ubuntu server with limited access.

## Step 1: Create a user account (Ubuntu server)

- sudo adduser claude

- Verify: getent passwd claude

## Step 2: Create a bash shell (Ubuntu server)

- sudo usermod -s /bin/bash claude

## Step 3: Unlock the user account to allow for key-based login (Ubuntu server)

- sudo passwd -u claude

- Verify: sudo passwd -S claude

## Step 4: Create SSH keys (Windows Powershell)

- ssh-keygen -t ed25519 -f $env:USERPROFILE\.ssh\claude_key -C "claude@servername"

## Step 5: Harden the private key's permissions

- Windows powershell:
                      icacls $env:USERPROFILE\.ssh\claude_key /inheritance:r

                      icacls $env:USERPROFILE\.ssh\claude_key /grant:r "$($env:USERNAME):F"

- Linux:
        chmod 600 ~/.ssh/claude_key

## Step 6: Transfer the public key to the Ubuntu server

- Windows powershell:
                      scp $env:USERPROFILE\.ssh\claude_key.pub <youruser@ip_address>:~/claude_key_temp.pub

## Step 7: Install the key and verify it

- Ubuntu server:
                sudo mkdir -p /home/claude/.ssh

                sudo mv ~/claude_key_temp.pub /home/claude/.ssh/authorized_keys

                sudo chown -R claude:claude /home/claude/.ssh

                sudo chmod 700 /home/claude/.ssh

                sudo chmod 600 /home/claude/.ssh/authorized_keys

- Verify on Windows powershell:
                                ssh-keygen -lf $env:USERPROFILE\.ssh\claude_key

- Verify on Ubuntu server:
                          sudo ssh-keygen -lf /home/claude/.ssh/authorized_keys

* These ssh fingerprints must match exactly.

## Step 8: Create an ssh alias

Windows powershell:
                  '~/.ssh/config` or `$env:USERPROFILE\.ssh\config

---

Host <name_of_alias>
    
     HostName <ip_address>
     
     User claude
     
     IdentityFile ~/.ssh/claude_key
     
     PreferredAuthentications publickey
     
     IdentitiesOnly yes

---

## Step 9: Test it

- Windows powershell:
                      ssh <alias>

    <img width="537" height="479" alt="Screenshot 2026-09-27 133538" src="https://github.com/user-attachments/assets/c842bfbb-11e8-47c0-aeb4-b38c32fe3b55" />


## Verification


<img width="1385" height="81" alt="Screenshot 2026-09-27 132720" src="https://github.com/user-attachments/assets/8dd6d2e9-9a57-48dd-abd2-f4ba7511cf77" />


## Troubleshooting

- I did not manage to take a photo in the heat of working through a few issues but the main problem I had was a rejected key when I tried to
  log in.

- To resolve this I eventually ran: getent passwd claude. This command revealed that the path to the key was wrong. I put in the correct path     and now claude can ssh into my server with restricted access.



                  




  

























