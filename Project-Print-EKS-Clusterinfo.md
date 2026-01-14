# Print EKS CLuster Info

### Introduction:

Let's assume:
- We have created 10 clusters in AWS.
- We want the below things from each cluster.
  - EKS Cluster Status?
  - Which Kubernetes Version?
  - Cluster endpoint?

Step1 : Create EKS Cluster
Step2: Implementation

```bash

import boto3

client = boto3.client('eks', region_name="eu-west-1")
clusters = client.list_cluster()['clusters']

for cluster in clusters:
    response = client.describe_cluster(
       name=cluster
    )
    cluster_info = response['cluster']
    cluster_status = cluster_info['status']
    cluster_endpoint = cluster_info['endpoint']
    cluster_version = cluster_info['version']
    print(f"Cluster {cluster} status is {cluster_status}")
    print(f"Cluster endpoint : {cluster_endpoint}")
    print(f"Cluster version : {cluster_version}")
