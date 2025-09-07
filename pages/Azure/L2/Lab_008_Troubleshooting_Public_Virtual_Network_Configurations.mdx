---
# sidebar_position: 03
title: Troubleshooting Public Virtual Network Configurations
description: Lab 08:- Troubleshooting Public Virtual Network Configurations
tags: ['azure', 'cloud', 'devops', 'kke', 'level2', 'task', 'lab08', 'azure cli', 'Virtual network', 'vnet']
---

------------------------------

- [Requirements](#requirements)
- [Steps](#steps)
- [Resources](#resources)

------------------------------

## Requirements

The Nautilus DevOps Team deployed an Nginx server on an Azure VM in a public VNet named xfusion-vnet. However, the server is still inaccessible from the internet.

As a DevOps team member, complete the following tasks:

1) Verify VNet Configuration: Ensure xfusion-vnet allows internet access.
2) Attach Public IP: A public IP named xfusion-pip already exists. Attach this public IP to the VM xfusion-vm to make it accessible from the internet.
3) Ensure Accessibility: Confirm the VM xfusion-vm is accessible on port 80.
4) Use the provided Azure credentials to troubleshoot and resolve the issue.
5) Use Azure cli

------------------------------

:::tip Note

The solution can be implemented using both the Azure Cloud Console and the Azure CLI. This document outlines the CLI-based approach to accomplish these tasks. It is recommended to first explore the Azure Cloud Console for hands-on experience and a practical understanding of the process before utilizing the CLI approach, unless specifically instructed otherwise.

:::

## Steps

```bash
# Set the resource group dynamically
RESOURCE_GROUP=$(az group list --query "[?contains(name, 'kml')].name" --output tsv)
PUBLIC_IP_NAME=devops-pip
VNET_NAME=devops-vnet
# List VNets in the resource group
az network vnet list --resource-group $RESOURCE_GROUP --query "[?name=='$VNET_NAME']" --output table

# Check NSGs associated with the VNet
az network nsg list --resource-group $RESOURCE_GROUP --query "[].{Name:name,Subnets:subnets}" --output table

# Check rules in the NSG
NSG_NAME=$(az network nsg list --resource-group $RESOURCE_GROUP --query "[0].name" --output tsv)
az network nsg rule list --resource-group $RESOURCE_GROUP --nsg-name $NSG_NAME --output table

# Add an inbound NSG rule for port 80 if not already present
az network nsg rule create \
    --resource-group $RESOURCE_GROUP \
    --nsg-name $NSG_NAME \
    --name AllowHTTP \
    --priority 100 \
    --protocol Tcp \
    --direction Inbound \
    --access Allow \
    --destination-port-ranges 80


# Get the NIC name for the VM
NIC_NAME=$(az vm show --resource-group $RESOURCE_GROUP --name devops-vm --query "networkProfile.networkInterfaces[0].id" --output tsv | awk -F '/' '{print $NF}')

# Attach the public IP to the NIC
az network nic ip-config update \
    --resource-group $RESOURCE_GROUP \
    --nic-name $NIC_NAME \
    --name ipconfig1 \
    --public-ip-address $PUBLIC_IP_NAME


# Find the route table name associated with the VNet (devops-vnet)
ROUTE_TABLE_NAME=$(az network vnet show --resource-group $RESOURCE_GROUP --name $VNET_NAME \
    --query "subnets[?routeTable.id != null].routeTable.id" --output tsv | awk -F '/' '{print $NF}')

if [ -z "$ROUTE_TABLE_NAME" ]; then
    echo "No route table is associated with the VNet $VNET_NAME. Exiting."
    exit 1
fi

echo "Route table identified: $ROUTE_TABLE_NAME"

# Get the route name dynamically
ROUTE_NAME=$(az network route-table route list --resource-group $RESOURCE_GROUP --route-table-name $ROUTE_TABLE_NAME \
    --query "[?contains(name, 'Block-Internet')].name" --output tsv)

if [ -z "$ROUTE_NAME" ]; then
    echo "No route named 'Block-Internet' found in the route table $ROUTE_TABLE_NAME. Exiting."
    exit 1
fi

echo "Route identified: $ROUTE_NAME"

# Check the current next hop type for the route
NEXT_HOP_TYPE=$(az network route-table route show \
    --resource-group $RESOURCE_GROUP \
    --route-table-name $ROUTE_TABLE_NAME \
    --name $ROUTE_NAME \
    --query "nextHopType" --output tsv)

if [ "$NEXT_HOP_TYPE" == "None" ]; then
    echo "Updating route '$ROUTE_NAME' to allow internet access..."
    
    # Update the route to set "Next hop type" as Internet
    az network route-table route update \
        --resource-group $RESOURCE_GROUP \
        --route-table-name $ROUTE_TABLE_NAME \
        --name $ROUTE_NAME \
        --next-hop-type Internet

    echo "Route updated successfully."
else
    echo "Route '$ROUTE_NAME' is already set to allow internet access. No changes needed."
fi

# Verify the update
echo "Verifying updated route settings..."
az network route-table route show \
    --resource-group $RESOURCE_GROUP \
    --route-table-name $ROUTE_TABLE_NAME \
    --name $ROUTE_NAME --output table


# Get the public IP address of the VM
VM_PUBLIC_IP=$(az network public-ip show --resource-group $RESOURCE_GROUP --name $PUBLIC_IP_NAME --query "ipAddress" --output tsv)

# Test connectivity
curl http://$VM_PUBLIC_IP


```

## Resources

[Azure CLI Docs](https://learn.microsoft.com/en-us/cli/azure/)

------------------------------
