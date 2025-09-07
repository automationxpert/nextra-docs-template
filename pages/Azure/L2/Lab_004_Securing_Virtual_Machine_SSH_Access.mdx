---
# sidebar_position: 03
title: Securing Virtual Machine SSH Access
description: Lab 004:- Securing Virtual Machine SSH Access
tags: ['azure', 'cloud', 'devops', 'kke', 'level2', 'task', 'lab04', 'azure cli', 'secure', 'ssh']
---

------------------------------

- [Requirements](#requirements)
- [Steps](#steps)
- [Resources](#resources)

------------------------------

## Requirements

The Nautilus DevOps team needs to set up a new Virtual Machine (VM) on the Azure cloud that can be accessed securely from their landing host (azure-client). Follow the steps below to complete this task:

1) Create an SSH Key: On the azure-client host, check if an SSH key already exists. If it doesn’t exist, create a new SSH key on the azure-client host that will be used for password-less SSH access.

2) Create a Virtual Machine: Use the Azure Portal or Azure CLI to create a new Virtual Machine named xfusion-vm in the westus region. Set the VM size to Standard_B1s and configure the VM with SSH access for the azureuser account using the newly created SSH key.

3) Configure SSH Access: Ensure that the SSH key from the azure-client host is added to the azureuser account on xfusion-vm, enabling secure, password-less SSH access from the azure-client host.

4) Verify Connectivity: Test the connection from azure-client to xfusion-vm using SSH to confirm that password-less access has been set up correctly.

5) Complete these tasks entirely with Azure CLI.

------------------------------

:::tip Note

The solution can be implemented using both the Azure Cloud Console and the Azure CLI. This document outlines the CLI-based approach to accomplish these tasks. It is recommended to first explore the Azure Cloud Console for hands-on experience and a practical understanding of the process before utilizing the CLI approach, unless specifically instructed otherwise.

:::

## Steps

```bash showLineNumbers
RESOURCE_GROUP=$(az group list --query "[?contains(name, 'kml')].name" --output tsv)
LOCATION="westus"
VM_NAME="xfusion-vm"
IMAGE="Ubuntu2404"
SIZE="Standard_B1s"
ADMIN_USERNAME="azureuser"
PUBLIC_IP_NAME="devops-pip"
SSH_KEY_PATH="$HOME/.ssh/id_rsa.pub"
SSH_KEY=$(cat $SSH_KEY_PATH)

# Generate SSH Key
ssh-keygen -t rsa -b 2048 -f $HOME/.ssh/id_rsa -q -N ""

# Create the VM with speciifed details
az vm create \
  --resource-group $RESOURCE_GROUP \
  --name $VM_NAME \
  --image $IMAGE \
  --size $SIZE \
  --admin-username $ADMIN_USERNAME \
  --ssh-key-values $SSH_KEY_PATH \
  --os-disk-size-gb 128 \
  --location $LOCATION  \
  --storage-sku Standard_LRS

# get the VM Public IP
VM_PUBLIC_IP=$(az vm list-ip-addresses --resource-group $RESOURCE_GROUP --name $VM_NAME --query "[].virtualMachine.network.publicIpAddresses[0].ipAddress" --output tsv)

# Check the ssh connection 
ssh $ADMIN_USERNAME@$VM_PUBLIC_IP
```

## Resources

[Azure CLI Docs](https://learn.microsoft.com/en-us/cli/azure/)

------------------------------
