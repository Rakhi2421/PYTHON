# Cleanup EC2 Snapshots

## Project Exercise: Cleanup Snapshots
- If scheduler runs everyday, we end with lots of snapshots

```bash
import boto3
from operator import itemgetter

ec2_client = boto3.client('ec2', region_name="eu-west-3")

volumes = ec2_client.describe_volumes(
    Filters=[
        {
              'Name': 'tag:Name',
              'Values': ['prod']
        }
    ]
)

for volume in volumes['Volumes']:


    snapshots = ec2_client.describe_snapshots(
        OwnerIds=['self']
        Filters=[
            {
                  'Name': 'volume-id',
                  'Values': [volume['VolumeId']]
            }
        ]
    )
sorted_by_date = sorted(snapshots, key=itemgetter('StartTime'), reverse=True)  - reverse key word is used to descending (latest to old), if we didn't use it then (old to latest) will print

for snap in snapshots['Snapshots']:
    print(snap['StartTime'])

print(################)

# to print all the snapshots in descending order (latest to old)
for snap in sorted_by_date:
    print(snap['StartTime'])

# To print list of snapshots by ignoring first 2
for snap in sorted_by_date[2:]:
    response = ec2_client.delete_snapshot(
        SnapshotId=snap['SnapshotId']
    )
    print(response)
    print(snap['StartTime'])
