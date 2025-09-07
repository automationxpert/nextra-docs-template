---
sidebar_position: 02
title: Configuring Instances with User Data
description: Lab 02 :-  Configuring Instances with User Data
#slug: /az-l2-t2
tags: ['azure', 'cloud', 'devops', 'kke', 'level2', 'task', 'lab02', 'configure instances']
---


- [Requirements](#requirements)
- [Steps](#steps)
- [Resources](#resources)

------------------------------

## Requirements

The Nautilus DevOps Team is working on setting up a new virtual machine (VM) to host a web server for a critical application. The team lead has requested you to create an Azure VM that will serve as a web server using Nginx. This VM will be part of the initial infrastructure setup for the Nautilus project. Ensuring that the server is correctly configured and accessible from the internet is crucial for the upcoming deployment phase.

As a member of the Nautilus DevOps Team, your task is to create a VM with the following specifications:

Instance Name: The VM must be named devops-vm.

Image: Use any available Ubuntu image to create this VM.

Custom Script Extension/User Data: Configure the VM to run a custom script during its launch. This script should:

Install the Nginx package.
Start the Nginx service.
Network Security Group (NSG): Ensure that the VM allows HTTP traffic on port 80 from the internet.

------------------------------

:::tip Note

The solution can be implemented using both the Azure Cloud Console and the Azure CLI. This document outlines the CLI-based approach to accomplish these tasks. It is recommended to first explore the Azure Cloud Console for hands-on experience and a practical understanding of the process before utilizing the CLI approach, unless specifically instructed otherwise.

:::

## Steps

```bash showLineNumbers
# Set Variables for Resources
RESOURCE_GROUP=$(az group list --query "[?contains(name, 'kml')].name" --output tsv)
VM_NAME="devops-vm"
LOCATION="eastus"
IMAGE="Ubuntu2404"
SIZE="Standard_B1s"
ADMIN_USERNAME="azureuser"
#PUBLIC_IP_NAME="devops-pip"
NSG_NAME="${VM_NAME}-nsg"
SSH_KEY_PATH="$HOME/.ssh/id_rsa.pub"
SSH_KEY=$(cat $SSH_KEY_PATH)

# Generate SSH Key
ssh-keygen -t rsa -b 2048 -f $HOME/.ssh/id_rsa -q -N ""

# Create a Network Security Group named $NSG_NAME:
az network nsg create \
 --resource-group $RESOURCE_GROUP \
 --name $NSG_NAME \
 --location $LOCATION

# Create a NSG RULE:
az network nsg rule create \
  --resource-group $RESOURCE_GROUP \
  --nsg-name $NSG_NAME \
  --name AllowHTTP \
  --priority 1000 \
  --protocol Tcp \
  --direction Inbound \
  --source-address-prefixes '*' \
  --source-port-ranges '*' \
  --destination-address-prefixes '*' \
  --destination-port-ranges 80 \
  --access Allow


# Create the VM with speciifed details
az vm create \
--resource-group $RESOURCE_GROUP \
--name $VM_NAME \
--image $IMAGE \
--admin-username $ADMIN_USERNAME \
--ssh-key-values $SSH_KEY_PATH \
--os-disk-size-gb 128 \
--location $LOCATION \
--storage-sku Standard_LRS \
--nsg $NSG_NAME \
--custom-data <(echo '#cloud-config
runcmd:
  - apt-get update
  - apt-get install -y nginx
  - systemctl start nginx
  - systemctl enable nginx')


# get the VM Public IP
VM_PUBLIC_IP=$(az vm list-ip-addresses --resource-group $RESOURCE_GROUP --name $VM_NAME --query "[].virtualMachine.network.publicIpAddresses[0].ipAddress" --output tsv)

# Check the nginx 
curl http://$VM_PUBLIC_IP
```

## Resources

[Azure CLI Docs](https://learn.microsoft.com/en-us/cli/azure/)

------------------------------
