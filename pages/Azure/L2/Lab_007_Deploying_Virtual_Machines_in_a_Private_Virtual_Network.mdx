---
# sidebar_position: 03
title: Deploying Virtual Machines in a Private Virtual Network
description: Lab 007:- Deploying Virtual Machines in a Private Virtual Network
tags: ['azure', 'cloud', 'devops', 'kke', 'level2', 'task', 'lab07', 'azure cli', 'private', 'vnet']
---


------------------------------

- [Requirements](#requirements)
- [Steps](#steps)
- [Resources](#resources)

------------------------------

## Requirements

The Nautilus DevOps team is expanding their Azure infrastructure and requires the setup of a private Virtual Network (VNet) along with a subnet. This VNet and subnet configuration will ensure that resources deployed within them remain isolated from external networks and can only communicate within the VNet. Additionally, the team needs to provision a Virtual Machine (VM) under the newly created private VNet. This VM should be accessible from within the VNet only, allowing for secure communication and resource management within the Azure environment.

The name of the VNet must be nautilus-priv-vnet, create a subnet named nautilus-priv-subnet under the same. Further, create a Virtual Machine named nautilus-priv-vm under this VNet. Additionally, create a Network Security Group (NSG) named nautilus-priv-nsg, and ensure that the NSG rules for the VM allow access only from within the VNet's CIDR block. Ensure all resources are created in the East US region.
use azurecli.

------------------------------

:::tip Note

The solution can be implemented using both the Azure Cloud Console and the Azure CLI. This document outlines the CLI-based approach to accomplish these tasks. It is recommended to first explore the Azure Cloud Console for hands-on experience and a practical understanding of the process before utilizing the CLI approach, unless specifically instructed otherwise.

:::

## Steps

```bash showLineNumbers
# Set variables
RESOURCE_GROUP=$(az group list --query "[?contains(name, 'kml')].name" --output tsv)
LOCATION="eastus"
VNET_NAME="nautilus-priv-vnet"
SUBNET_NAME="nautilus-priv-subnet"
VM_NAME="nautilus-priv-vm"
NSG_NAME="nautilus-priv-nsg"
ADDRESS_SPACE="10.0.0.0/16"
SUBNET_PREFIX="10.0.1.0/24"

# Generate SSH Key
ssh-keygen -t rsa -b 2048 -f $HOME/.ssh/id_rsa -q -N ""

# Create Virtual Network
az network vnet create \
  --resource-group $RESOURCE_GROUP \
  --name $VNET_NAME \
  --address-prefix $ADDRESS_SPACE \
  --subnet-name $SUBNET_NAME \
  --subnet-prefix $SUBNET_PREFIX \
  --location "$LOCATION"

# Create Network Security Group
az network nsg create \
  --resource-group $RESOURCE_GROUP \
  --name $NSG_NAME \
  --location "$LOCATION"

# Create an NSG rule to allow traffic only within the VNet CIDR block
az network nsg rule create \
  --resource-group $RESOURCE_GROUP \
  --nsg-name $NSG_NAME \
  --name AllowVNetInBound \
  --priority 100 \
  --access Allow \
  --direction Inbound \
  --protocol "*" \
  --source-address-prefixes $ADDRESS_SPACE \
  --destination-address-prefixes $ADDRESS_SPACE \
  --source-port-ranges "*" \
  --destination-port-ranges "*"

# Associate the NSG with the subnet
az network vnet subnet update \
  --resource-group $RESOURCE_GROUP \
  --vnet-name $VNET_NAME \
  --name $SUBNET_NAME \
  --network-security-group $NSG_NAME

# Create a Virtual Machine
az vm create \
  --resource-group $RESOURCE_GROUP \
  --name $VM_NAME \
  --vnet-name $VNET_NAME \
  --subnet $SUBNET_NAME \
  --image Ubuntu2404 \
  --admin-username azureuser \
  --generate-ssh-keys \
  --location "$LOCATION"
  --os-disk-size-gb 128 \
  --location $LOCATION  \
  --storage-sku Standard_LRS

# Output the details
echo "Resources created successfully:"
echo "- Virtual Network: $VNET_NAME"
echo "- Subnet: $SUBNET_NAME"
echo "- Network Security Group: $NSG_NAME"
echo "- Virtual Machine: $VM_NAME"

# Output the status
echo "VM is being created and will be accessible only within the VNet."
```

## Resources

[Azure CLI Docs](https://learn.microsoft.com/en-us/cli/azure/)

------------------------------
