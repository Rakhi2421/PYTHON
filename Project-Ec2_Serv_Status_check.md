# EC2 Server status check using Python

## Project Introduction

Lets assume:
- created hundreds of ec2 servers with terraform
- Autoscaling configured
- new instances get created/deleted all the time.
- new instance always need some time to initialize
- So, here we want to know which server is in running state, which is in initialize state, which is terminated.

Step 1: Create 3 EC2 instances using terraform 

Implementation:  

Step 2: Print EC2 Instance state.
```bash

import boto3

ec2_client = boto3.client('ec2', region_name="eu-central-1")
ec2_resource   = boto3.resource('ec2', region_name="eu-central-1")

reservations = ec2_client.describe_instances()
for reservation in reservations['Reservarions']:
    instances = reservation['Instances']
    for instance in instances:
        print(f"Instance {instance['InstanceId']} is {instance['State']['Name']}")
```
Step 3: Print EC2 Status Check

```bash

import boto3

ec2_client = boto3.client('ec2', region_name="eu-central-1")
ec2_resource   = boto3.resource('ec2', region_name="eu-central-1")

reservations = ec2_client.describe_instances()
for reservation in reservations['Reservarions']:
    instances = reservation['Instances']
    for instance in instances:
        print(f"Instance {instance['InstanceId']} is {instance['State']['Name']}")

statuses = ec2_client.describe_instance_status()
for status in statuses['InstanceStatuses']:
    ins_status = status['InstanceStatus']['Status']
    sys_status = status['SystemStatus']['Status']
    print(f"Instance {status['InstanceId']} status is {ins_status} and system status is {sys_status}")
```  

Improving:
Step4: Get everything in 1 AWS API CALL.

```bash

import boto3

ec2_client = boto3.client('ec2', region_name="eu-central-1")
ec2_resource   = boto3.resource('ec2', region_name="eu-central-1")

reservations = ec2_client.describe_instances()
for reservation in reservations['Reservarions']:
    instances = reservation['Instances']
    for instance in instances:
        print(f"Instance {instance['InstanceId']} is {instance['State']['Name']}")

statuses = ec2_client.describe_instance_status()
for status in statuses['InstanceStatuses']:
    ins_status = status['InstanceStatus']['Status']
    sys_status = status['SystemStatus']['Status']
    state = status['InstanceState']['Name']
    print(f"Instance {status['InstanceId']} status is {state} with instance status {ins_status} and system status  {sys_status}")
```  

