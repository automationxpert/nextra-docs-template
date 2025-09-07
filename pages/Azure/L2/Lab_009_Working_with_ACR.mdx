---
# sidebar_position: 03
title: Working with Azure Container Registry
description: Lab 09:- Working with Azure Container Registry
tags: ['azure', 'cloud', 'devops', 'kke', 'level2', 'task', 'lab09', 'azure cli', 'acr']
---

------------------------------

- [Requirements](#requirements)
- [Steps](#steps)
- [Resources](#resources)

------------------------------

## Requirements

The Nautilus DevOps team has been tasked with setting up a containerized application. They need to create a Azure Container Registry (ACR) to store their Docker images. Once the repository is created, they will build a Docker image from a Dockerfile located on the azure-client host and push this image to the ACR repository. This process is essential for maintaining and deploying containerized applications in a streamlined manner.

1) Create a ACR repository named devopsacr26050 under East US.

2) Pricing plan must be Basic.

3) Dockerfile already exists under /root/pyapp directory on azure-client host.

4) Build a Docker image using this Dockerfile and push the same to the newly created ACR repo. The image tag must be latest i.e devopsacr26050:latest.

------------------------------

:::tip Note

The solution can be implemented using both the Azure Cloud Console and the Azure CLI. This document outlines the CLI-based approach to accomplish these tasks. It is recommended to first explore the Azure Cloud Console for hands-on experience and a practical understanding of the process before utilizing the CLI approach, unless specifically instructed otherwise.

:::

## Steps

```bash showLineNumbers
#!/bin/bash

# Step 1: Set Variables
ACR_NAME="devopsacr26050"
RESOURCE_GROUP=$(az group list --query "[?contains(name, 'kml')].name" --output tsv)
LOCATION="eastus"
SKU="Basic"
DOCKERFILE_PATH="/root/pyapp"
IMAGE_NAME=$ACR_NAME
IMAGE_TAG="$ACR_NAME.azurecr.io/$IMAGE_NAME:latest"

# Step 2: Create Azure Container Registry
echo "Creating Azure Container Registry..."
az acr create --resource-group $RESOURCE_GROUP --name $ACR_NAME --sku $SKU --location "$LOCATION"

if [ $? -ne 0 ]; then
    echo "Failed to create Azure Container Registry. Please check the error and try again."
    exit 1
fi

echo "Azure Container Registry '$ACR_NAME' created successfully."

# Step 3: Log in to Azure Container Registry
echo "Logging in to Azure Container Registry..."
az acr login --name $ACR_NAME

if [ $? -ne 0 ]; then
    echo "Failed to log in to ACR. Please check your credentials."
    exit 1
fi

# Step 4: Build the Docker Image
echo "Building Docker image from Dockerfile at $DOCKERFILE_PATH..."
docker build -t $IMAGE_TAG $DOCKERFILE_PATH

if [ $? -ne 0 ]; then
    echo "Failed to build Docker image. Please check the Dockerfile and try again."
    exit 1
fi

echo "Docker image built successfully with tag '$IMAGE_TAG'."

# Step 5: Push the Docker Image to ACR
echo "Pushing Docker image to Azure Container Registry..."
docker push $IMAGE_TAG

if [ $? -eq 0 ]; then
    echo "Docker image pushed successfully to ACR with tag '$IMAGE_TAG'."
else
    echo "Failed to push Docker image. Please check the error and try again."
    exit 1
fi

```

## Resources

[Azure CLI Docs](https://learn.microsoft.com/en-us/cli/azure/)

------------------------------
