# AWS EKS Deployment 

This deployment is done with reference to the official documentation from Hashicorp to deploy EKS cluster to AWS.
# Steps invovled in the entire deployment 

1. A VPC is created to isolate the resources from any other resources that might be running.
2. Three private and public subnets are also created across different AZ's along with NAT gateway for private subnets to access the internet.
3. Three security groups are created with the specified cidr for the inbound traffic. For the outbound rules, all the subnets will have cidr blocks as 0.0.0.0/0 
4. For the EKS cluster, 2 worker groups are created, with 2 autoscaling groups. One with 2 t2.small instances and 1 t2.medium instance as desired capacity.
5. All the instances are created in a private subnet with differnet AZ. 
6. A General Purpose volume (GP2) is also used for storage (Default size is 100 GB) So a total of 300 GB is provisioned.
7. A output file is written so that the values of the variables can be used later or can be referenced by another terraform file, along with a kubernetes RBAC yaml    file for deploying the kubernetes dashboard.