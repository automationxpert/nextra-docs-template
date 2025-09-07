---
# sidebar_position: 03
title: Create Key Pair
description: Lab 001:- Create Key Pair
tags: ['aws', 'cloud', 'devops', 'kke', 'level1', 'task', 'lab01', 'aws cli', 'ssh key pair']
---


- [Requirements](#requirements)
- [Steps](#steps)
- [Resources](#resources)

------------------------------

## Requirements

The Nautilus DevOps team is strategizing the migration of a portion of their infrastructure to the AWS cloud. Recognizing the scale of this undertaking, they have opted to approach the migration in incremental steps rather than as a single massive transition. To achieve this, they have segmented large tasks into smaller, more manageable units. This granular approach enables the team to execute the migration in gradual phases, ensuring smoother implementation and minimizing disruption to ongoing operations. By breaking down the migration into smaller tasks, the Nautilus DevOps team can systematically progress through each stage, allowing for better control, risk mitigation, and optimization of resources throughout the migration process.

For this task, create a key pair with the following requirements:

1) Name of the key pair should be devops-kp.

2) Key pair type must be rsa

:::tip Note

The solution can be implemented using both the AWS Cloud Console and the AWS CLI. This document outlines the CLI-based approach to accomplish these tasks. It is recommended to first explore the AWS Cloud Console for hands-on experience and a practical understanding of the process before utilizing the CLI approach, unless specifically instructed otherwise.

:::

## Steps

To create a key pair named `devops-kp` with the type `rsa` using the AWS CLI, follow these steps:

**Define variables** for the key pair name and key pair type:

```sh
KEY_PAIR_NAME="devops-kp"
KEY_PAIR_TYPE="rsa"
```

**Create the key pair** and save the private key to a file:

```sh
aws ec2 create-key-pair --key-name $KEY_PAIR_NAME --key-type $KEY_PAIR_TYPE --query "KeyMaterial" --output text > ${KEY_PAIR_NAME}.pem
```

**Set the correct permissions on the private key file**:

```sh
chmod 400 ${KEY_PAIR_NAME}.pem
```

**Validate the key pair creation**:

```sh
aws ec2 describe-key-pairs --key-name $KEY_PAIR_NAME
```

Here is the complete script with all the steps combined:

```sh
# Define variables for the key pair name and key pair type
KEY_PAIR_NAME="devops-kp"
KEY_PAIR_TYPE="rsa"

# Create the key pair and save the private key to a file
aws ec2 create-key-pair --key-name $KEY_PAIR_NAME --key-type $KEY_PAIR_TYPE --query "KeyMaterial" --output text > ${KEY_PAIR_NAME}.pem

# Set the correct permissions on the private key file
chmod 400 ${KEY_PAIR_NAME}.pem

# Validate the key pair creation
aws ec2 describe-key-pairs --key-name $KEY_PAIR_NAME
```

**Validation Output:**

The `aws ec2 describe-key-pairs` command should return details about the key pair, confirming that it has been successfully created.

```json
{
    "KeyPairs": [
        {
            "KeyName": "devops-kp",
            "KeyPairId": "key-xxxxxxxxxxxxxxx",
            "KeyType": "rsa",
            "KeyFingerprint": "xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx"
        }
    ]
}
```

This confirms that the key pair `devops-kp` has been successfully created with the type `rsa`, and the private key has been saved to a file named `devops-kp.pem` with the correct permissions set.

## Resources

[AWS CLI Docs](https://aws.amazon.com/cli/)

------------------------------
