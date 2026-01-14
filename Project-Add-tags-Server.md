# ADD TAGS TO EC2 Servers.

### Introduction:

Lets Assume: 
- We have 20 servers in paris region that we use as production servers.
- we have 10 servers in mum region that we use as development servers.
- Those were created using terraform.
- Now, We want to add environmental tags to all the EC2 servers.

### Implementation:

import boto3

ec2_client_Paris = boto3.client('ec2',region_name="eu-west-3")
ec2_resource_Paris = boto3.resource('ec2',region_name="eu-west-3")

ec2_client_Mum = boto3.client('ec2',region_name="eu-North-1")
ec2_resource_Mum = boto3.resource('ec2',region_name="eu-North-1")

instance_ids_paris = []
instance_ids_mum = []

reservations_paris = ec2_client_paris.describe_instances()['Reservations']
for res in reservation_paris:
    instances = res['Instances']
    for ins in instances:
        instance_ids_paris.append(ins['InstanceId'])
response = ec2_resource_paris.create_tags(
   Resources=instance_ids_paris,
   Tags=[
       {
           'key' : 'environment',
           'value' : 'prod'
       },
   ]
)

reservations_mum = ec2_client_mum.describe_instances()['Reservations']
for res in reservation_mum:
    instances = res['Instances']
    for ins in instances:
        instance_ids_mum.append(ins['InstanceId'])
response = ec2_resource_mum.create_tags(
   Resources=instance_ids_mum,
   Tags=[
       {
           'key' : 'environment',
           'value' : 'dev'
       },
   ]
)
