# Restore EC2 Volume 

Project Exercise: Restore EC2 Volume.  

Lets assume:
 - our existing server volume is corrupted.
 - we want to recover the latest working state
Step1: Create new Volume from the snapshot
Step2: Attach new volume to the instance

```bash

import boto3

ec2_client = boto3.client('ec2', region_name="eu-west-3")
ec2_resource = boto3.resource('ec2', region_name="eu-west-3")

instance_id = "i-04f01d6d78fd78995d67s8"

#1. Get Volume of EC2 Instance
# 2. Get Snapshot of Volume
volumes = ec2_client.describe_volumes(
    Filters=[
        {
             'Name': 'attachment.instance_id',
             'Values': [instance_id]
        }
    ]
)

instance_volume = volumes['Volumes'][0]
print(instance_volume)

ec2_client.describe_snapshots(
    OwnerIds=['self']
    Filters=[
        {
             'Name': 'volume-id',
             'Values': [instance_volume['VolumeId']]
        }
    ]
)

latest_snapshot = sorted(snapshots['Snapshots'], key=itemgetter('StartTime'), reverse=True)[0]
print(latest_snapshot['StartTime'])

new_volume = ec2_client.create_volume(
    SnapshotId=latest_snapshot['SnapshotId'],
    AvailabilityZone="eu-west-3b",
    TagSpecifications=[
       {
            'ResourceType': 'volume',
            'Tags': [
                {
                    'Key': 'Name'
                    'Value': 'prod'
                }
            ]
       }
    ]
)

while True:
    vol = ec2_resource.Volume(new_volume['VolumeId'])
    print(vol.state)
    if vol.state == "available":
       ec2_resource.Instance(instance_id).attach_volume(
       VolumeId=new_volume['VolumeId'],
       Device='/dev/xvdb'
       )
       break
```
