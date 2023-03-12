# packer-proxmox-templates
# Deploying Proxmox Templates via Packer
Packer allow us to deploy a VM Template in Proxmox just with an ISO file. Therefore, we can deploy terraform VM's fastly from this VM template. Packer is also very powerfull because we can set up in advance our predefined users or whatever package we will want in our future deployments. 


## Credentials
This repo must contains a file called credentials.pkr.hcl with the following content: 

```hcl
proxmox_api_url          = "https://0.0.0.0:8006/api2/json" # Your Proxmox IP Address
proxmox_api_token_id     = "user@pam!terraform"                   # API Token ID
proxmox_api_token_secret = "token"
```

Chaning this values for whatever it takes in your case. 

## Execution


```bash
packer build -var-file='..\credentials.pkr.hcl' .\ubuntu-server-focal.pkr.hcl #The process can take ~20 minutes perfectly
```
It is very import to watch out Firewall rule for incoming traffic from Proxmox to Packer host because our proxmox will need conexion to our Packer Host. 

Inside the ubuntu-server-focal folder we define the deployment via ISO (which have to be uploaded in the Proxmox Server) or it can be configured to be downloaded from the internet. Next, in the http/user-data.yml we define some cloud-init config necessary to ensure that template exposes SSH service and some cool things like passing our public SSH key to be able to connect via ssh in each one of the VM's that will be deployed with Terraform. 
