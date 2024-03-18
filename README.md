
# AWS Serverless Infrastructure

## Overview

This documentation provides an overview and setup instructions for a serverless AWS infrastructure that uses AWS Lambda for computing, Amazon S3 for storage, and AWS KMS for encryption. An API Gateway serves as the entry point for user requests, triggering the Lambda functions.

## Architecture Diagram

Below is the architecture diagram representing the serverless setup:

![Ar](https://github.com/HashTekSolutions/s3-lambda-api/assets/113921841/f2efefb6-48ca-4275-96a6-c14b8a4694aa)


The architecture includes the following components:
- **User**: Initiates the process by making a request to the API Gateway.
- **API Gateway**: Routes incoming user requests to the appropriate Lambda function.
- **Lambda Function 1**: Triggered by the EventBridge for scheduled tasks, such as encryption using KMS.
- **Lambda Function 2**: Handles user requests to retrieve data, fetching encrypted content from S3.
- **Amazon S3**: Stores encrypted data objects.
- **AWS KMS**: Manages encryption keys for securing data.
- **EventBridge**: Schedules and triggers Lambda Function 1.

## Project Structure

The Terraform project is organized as follows:

```
terraform-project/
│
├── modules/          # Reusable Terraform modules.
│   ├── kms/          # KMS key configurations.
│   ├── s3/           # S3 bucket setups.
│   ├── lambda/       # Lambda function definitions.
│   ├── iam/          # IAM role and policy specifications.
│   └── api_gateway/  # API Gateway resources.
│
└── env/     # Environment-specific configs.
    ├── dev/  
         ├── main.tf           # Main Terraform configuration.
         ├── variables.tf      # Variable definitions.
         ├── outputs.tf        # Output values.
         ├── providers.tf        # Development environment.
    
```

## Setup and Deployment

### Prerequisites
- AWS CLI with appropriate access rights.
- Terraform installed on your local machine.

### Steps
1. **Initialization**: Run `terraform init` within the environment directory to initialize Terraform.
2. **Plan**: Execute `terraform plan` to review the changes to be applied.
3. **Apply**: Use `terraform apply` to provision the resources on AWS.
4. **Verify**: After deployment, test the API using the provided endpoint URL.

you can use this url end point : lambda_api_endpoint = ** "https://mmt73opuqa.execute-api.eu-north-1.amazonaws.com/dev/retrieve_most_recent_object_dev" ** fet the latest s3 object
