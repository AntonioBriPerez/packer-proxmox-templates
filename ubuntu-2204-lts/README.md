To execute 22.04 template you need a file called "secrets.json" with the following content: 
```json
{
    "proxmox_username": "root@pam",
    "proxmox_password": "123"
}
```
The proxmox password is the password you use to access web UI and then execute: 
```bash
packer build -var-file='secrets.json' .\ubuntu.json
```