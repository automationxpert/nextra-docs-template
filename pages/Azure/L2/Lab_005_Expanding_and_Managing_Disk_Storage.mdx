---
# sidebar_position: 03
title: Expanding and Managing Disk Storage
description: Lab 05:- Expanding and Managing Disk Storage
tags: ['azure', 'cloud', 'devops', 'kke', 'level2', 'task', 'lab05', 'azure cli', 'disk management', 'expanding disk']
---

------------------------------

- [Requirements](#requirements)
- [Steps](#steps)
- [Resources](#resources)

------------------------------

## Requirements

1) Expand the existing VM datacenter-vm disk from 32Gi to 64Gi.

2) Also create a new standard HDD data disk named datacenter-disk of 64Gi and mount the disk to VM datacenter-vm at location /mnt/datacenter-disk.

------------------------------

:::tip Note

The solution can be implemented using both the Azure Cloud Console and the Azure CLI. This document outlines the CLI-based approach to accomplish these tasks. It is recommended to first explore the Azure Cloud Console for hands-on experience and a practical understanding of the process before utilizing the CLI approach, unless specifically instructed otherwise.

:::

## Steps

```bash showLineNumbers
RESOURCE_GROUP=$(az group list --query "[?contains(name, 'kml')].name" --output tsv)
VM_NAME='datacenter-vm'
DISK_NEW_SIZE=64
ADMIN_USERNAME="azureuser"
$NEW_DISKNAME='datacenter-disk'
MOUNTPOINT='/mnt/datacenter-disk'

OS_DISK_NAME = $(az vm show \
  --resource-group $RESOURCE_GROUP \
  --name datacenter-vm \
  --query "storageProfile.osDisk.name" \
  -o tsv)

# get the VM Public IP
VM_PUBLIC_IP=$(az vm list-ip-addresses --resource-group $RESOURCE_GROUP --name $VM_NAME --query "[].virtualMachine.network.publicIpAddresses[0].ipAddress" --output tsv)

# Power Off the VM
az vm stop --resource-group MyResourceGroup --name $VM_NAME

# Set the OS DISK to 64 GB
az disk update \
  --resource-group $RESOURCE_GROUP \
  --name $OS_DISK_NAME \
  --size-gb $DISK_NEW_SIZE

# Power On the VM
az vm start --resource-group MyResourceGroup --name $VM_NAME

# Create a new 64GiB data disk:
az disk create \
  --resource-group $RESOURCE_GROUP \
  --name $NEW_DISKNAME \
  --size-gb 64 \
  --sku Standard_LRS

# Attach the disk to the VM:

az vm disk attach \
  --resource-group $RESOURCE_GROUP \
  --vm-name datacenter-vm \
  --name datacenter-disk \
  --new
```

Login to vm ```bash ssh $ADMIN_USERNAME@$VM_PUBLIC_IP``` and execute the below from inside the VM.

```bash showLineNumbers
## 
lsblk

# Look for a new disk (e.g., /dev/sdc).
# Format the disk:
sudo mkfs.ext4 /dev/sdc

# Create a mount point:
sudo mkdir -p /mnt/datacenter-disk

# Mount the disk:
sudo mount /dev/sdc $MOUNTPOINT

# Add to /etc/fstab for persistence: Get the disk's UUID:
sudo blkid /dev/sdc

# Add the following line to /etc/fstab:
UUID=<disk-uuid> /mnt/datacenter-disk ext4 defaults,nofail 0 2

# Verify the Mount:
df -h

```

## Resources

[Azure CLI Docs](https://learn.microsoft.com/en-us/cli/azure/)

------------------------------
