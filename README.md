# Amazon RDS creation and S3 backend configuartion
This infrastructure is used to create a MySQL RDS database. Moreover, the state file is stored in a S3 bucket and state locking is ensured by another RDS database.

**Files:**
1. [`main.tf`](https://github.com/Sebastianutcn/s3_backend/blob/main/main.tf) is used to provision the RDS database, along with the VPC, Subnets, and Security Groups to allow inbound traffic only for HTTP (80) and MySQL Aurora (3306).
2. [`state.tf`](https://github.com/Sebastianutcn/s3_backend/blob/main/state.tf) is used to create the KMS key, the S3 bucket used to store the remote state, and the DynamoDB table used to lock the state.
3. [`provider.tf`](https://github.com/Sebastianutcn/s3_backend/blob/main/provider.tf) is used to provision the deploy stage and the IAM roles for it. The deployment is done by an EC2 instance.

## Installation
- Terraform command to initialize the project
```
terraform init
```
* Terraform command to plan the changes and to check again the resources that were added, changed or deleted
```
terraform plan -out plan.out
```
- Terraform command to apply the changes
```
terraform apply plan.out --auto-approve
```
