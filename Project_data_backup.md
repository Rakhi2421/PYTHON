# Data Backup

Automating data backup of EC2 Instances
- Create Snapshot of  Volumes.
  - Volumes are AWS Storage components = Stores EC2 Instance data
  - Volume Snapshot = copy of volume

Step1: Create 2 EC2 Instances.
Step2: Implementation

```bash
import boto3
import scheduler

ec2_client = boto3.client('ec2', region_name="eu-west-1")

def create_volume_snapshots():
    volumes = ec2_client.describe_volumes(
        Filters=[
            {
                'Name' : 'tag:Name',
                'Values' : ['prod','staging']
            }
        ]
    )
    for volume in volumes['Volumes']:
        new_snapshot = ec2_client.create_snapshot(
            VolumeId=volume['VolumeId']
        )
        print(new_snashot)

schedule.every().day.do(create_volume_snapshots)

while True:
    schedule.run_pending()
```
