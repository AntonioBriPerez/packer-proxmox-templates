# packer-proxmox-templates
## Execution


```
packer build -var-file='..\credentials.pkr.hcl' .\ubuntu-server-focal.pkr.hcl
```
Watch out Firewall rule for incoming traffic from Proxmox to Packer host!!!