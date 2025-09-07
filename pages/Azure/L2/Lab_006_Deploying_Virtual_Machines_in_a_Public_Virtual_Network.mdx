---
# sidebar_position: 03
title: Deploying Virtual Machines in a Public Virtual Network
description: Lab 06:- Deploying Virtual Machines in a Public Virtual Network
tags: ['azure', 'cloud', 'devops', 'kke', 'level2', 'task', 'lab06', 'azure cli', 'Virtual network', 'vnet']
---

------------------------------

- [Requirements](#requirements)
- [Steps](#steps)
- [Resources](#resources)

------------------------------

## Requirements

The Nautilus DevOps Team has received a request from the Networking Team to set up a new public VNet to support a set of public-facing services. This VNet will host various resources that need to be accessible over the internet. As part of this setup, you need to ensure the VNet has public subnets with automatic public IP assignment for resources. Additionally, a new VM will be launched within this VNet to host public applications that require SSH access. This setup will enable the Networking Team to deploy and manage public-facing applications.

Create a public VNet named datacenter-pub-vnet, and a subnet named datacenter-pub-subnet under the same, make sure public IP is being auto-assigned to resources under this subnet. Further, create a VM named datacenter-pub-vm under this VNet. Make sure SSH port 22 is open for this instance and accessible over the internet. Use the Azure portal to complete the task and ensure that SSH access is configured correctly.

------------------------------

:::tip Note

The solution can be implemented using both the Azure Cloud Console and the Azure CLI. This document outlines the CLI-based approach to accomplish these tasks. It is recommended to first explore the Azure Cloud Console for hands-on experience and a practical understanding of the process before utilizing the CLI approach, unless specifically instructed otherwise.

:::

## Steps

```bash showLineNumbers

#!/bin/bash

# Set variables
RESOURCE_GROUP=$(az group list --query "[?contains(name, 'kml')].name" --output tsv)
LOCATION="eastus"
VNET_NAME="datacenter-pub-vnet"
SUBNET_NAME="datacenter-pub-subnet"
VM_NAME="datacenter-pub-vm"
VM_SIZE="Standard_B1s"
PUBLIC_IP_NAME="datacenter-pub-pip"
NSG_NAME="datacenter-pub-nsg"
SSH_KEY_PATH="$HOME/.ssh/id_rsa.pub"
SSH_KEY=SSH_KEY=$(cat $SSH_KEY_PATH)

# Create the VNet and subnet
az network vnet create --resource-group $RESOURCE_GROUP --name $VNET_NAME --address-prefix 10.0.0.0/16 --subnet-name $SUBNET_NAME --subnet-prefix 10.0.1.0/24 --location $LOCATION 

# Create a Network Security Group (NSG) and allow SSH access
az network nsg create --resource-group $RESOURCE_GROUP --name $NSG_NAME --location $LOCATION 

az network nsg rule create --resource-group $RESOURCE_GROUP --nsg-name $NSG_NAME --name Allow-SSH --protocol Tcp --direction Inbound --priority 1000 --source-address-prefixes '*' --source-port-ranges '*' --destination-address-prefixes '*' --destination-port-ranges 22 --access Allow --location $LOCATION 

# Create a public IP address
az network public-ip create --resource-group $RESOURCE_GROUP --name $PUBLIC_IP_NAME --allocation-method Static --location $LOCATION 

# Create a NIC with the NSG and public IP
az network nic create --resource-group $RESOURCE_GROUP --name ${VM_NAME}-nic --vnet-name $VNET_NAME --subnet $SUBNET_NAME --network-security-group $NSG_NAME --public-ip-address $PUBLIC_IP_NAME --location $LOCATION 

# Create the VM with the specified SSH key
az vm create \
  --resource-group $RESOURCE_GROUP \
  --name $VM_NAME \
  --nics ${VM_NAME}-nic \
  --image Ubuntu2404 \
  --size $VM_SIZE \
  --admin-username azureuser \
  --ssh-key-values $SSH_KEY_PATH \
  --os-disk-size-gb 128 \
  --location $LOCATION  \
  --storage-sku Standard_LRS
  
# Get the public IP address
PUBLIC_IP=$(az vm show --resource-group $RESOURCE_GROUP --name $VM_NAME --show-details --query [publicIps] --output tsv)

# Output the public IP address
echo "VM is created and accessible via SSH at: $PUBLIC_IP"
```

## Resources

[Azure CLI Docs](https://learn.microsoft.com/en-us/cli/azure/)

------------------------------
