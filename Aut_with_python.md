#Automation with Python

## Module Overview
#### Cloud Automation
  Automating Tasks on AWS
   - Introduction to boto (AWS SDK for python)
   - Install Boto and connect to aws
   - Creating VPC and Subnets
   - Difference of terraform and python
Automating taks around EC2 Instances
 - Status checks of EC2 Instances
 - Configure server: Add tags to EC2 Instances
 - Backup and cleanup EC2 Volumes
 - Restore EC2 Volume from backup
 - Write Scheduled tasks
EKS Cluster Information
WEBSITE Monitoring
- Monitor Application
- Email Notification
- Recover: Restart application

Introduction to automating maintainance tasks on AWS
- doing regular backups
- doing regular cleanups
- configuration on existing servers
- doing health checks/monitoring

# Install boto3 and connect to aws

Named Parameters:
- pass arguments via key=value
- also called "key arguments"
- this way the order of parameters does not matter

```bash
$: pip install boto3
Configure aws credentials using the following command in local, where we are using python : aws configure

# code to get the existing VPC details from our aws account
# main.py

import boto3

ec2_client = boto3.client('ec2', region_name="eu-central-1")

all_available_vpcs = ec2_client.describe_vpcs()
vpcs = all_available_vpcs["Vpcs"]

for vpc in vpcs:
    print(vpc["VpcId"])
    cidr_block_assoc_sets = vpc["CidrBlockAssociationSet"]
    for assoc_set in cidr_block_assoc_sets:
        print(assoc_set["CidrBlockState"])
```

## Create VPC and Subnets

| client | resource |
|---------|----------|
| more-low-level-api | high-level & object- oriented |
| provides one-to-one mapping to underlying HTTP API operations | provides resource objects to access attributes and perform actions |

```bash

# main.py

## Resource returns a Resource object, we can use for subsequent calls

import boto3

ec2_client = boto3.client('ec2', region_name="eu-central-1")
ec2_resource = boto3.resource('ec2', region_name="eu-central-1")

new_vpc = ec2_resource.create_vpc(
    CidrBlock="10.0.0.0/16"
)
new_vpc.create_subnet(
    CidrBlock="10.0.1.0/24"
)
new_vpc.create_subnet(
    CidrBlock="10.0.2.0/24"
)
new_vpc.create_tags(
    Tags=[
         {
             'key' : 'Name',
             'value' : 'my-vpc'
         },
    ]
)

all_available_vpcs = ec2_client.describe_vpcs()
vpcs = all_available_vpcs["Vpcs"]

for vpc in vpcs:
    print(vpc["VpcId"])
    cidr_block_assoc_sets = vpc["CidrBlockAssociationSet"]
    for assoc_set in cidr_block_assoc_sets:
        print(assoc_set["CidrBlockState"])
```

## Terraform vs Python
TF advantages for Infrastructure provisioning

| Terraform Infrastructure Provisioning | Python |
|--------------------|--------------------------|
| Terraform manages state of infrastructure | Python doesn't have a state file |
| Terraform knows the current state | Python doesn't know the current state |
| Terraform knows the difference of the current state and your configured/desired state | Python doesn't know the difference |
| Terraorm is idempotent (Idempotent means multiple execution of same config file, will always result in same end result) | Python is not idempotent |
| Terraform is more high-level | Python uses low level api |
