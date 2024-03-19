## Serverless Architecture: 
This project leverages the power of serverless computing on AWS. It utilizes AWS Lambda functions to execute code without managing servers. This offers scalability, cost-efficiency, and faster development cycles.

## Architecture Diagram

Below is the architecture diagram representing the serverless setup:

![Ar](https://github.com/HashTekSolutions/s3-lambda-api/assets/113921841/f2efefb6-48ca-4275-96a6-c14b8a4694aa)


# Components we used here:
### AWS Lambda Functions: 
The project utilizes two Lambda functions:
### Function 1 (Triggered by EventBridge): 
This function likely handles scheduled tasks. EventBridge, a serverless event bus, triggers this function based on a predefined schedule. The function might perform actions like data encryption using AWS KMS.
### Function 2 (Triggered by API Gateway):
This function handles user requests received through the API Gateway. It retrieves data, possibly fetching encrypted content from Amazon S3.
### Amazon S3:
This service acts as the storage layer. It securely stores the data objects in an encrypted format.
### AWS KMS: 
This service manages encryption keys used to secure the data at rest in S3. It ensures only authorized entities can access the data.
### API Gateway:
This service serves as the front door for user requests. It routes incoming requests to the appropriate Lambda function based on predefined configurations.


## Architectural Advantages
This serverless architecture offers several benefits:

### Scalability: 
AWS automatically scales the Lambda functions based on traffic, ensuring smooth operation even during high loads.
### Cost-Effectiveness:
You only pay for the resources you use. Since server management is eliminated, the infrastructure incurs minimal cost during idle periods.
### Increased Developer Agility:
Serverless development allows developers to focus on writing code without worrying about server provisioning and maintenance.


## Project Structure Analysis

The project leverages Terraform for infrastructure management. Terraform offers a declarative approach, where you define the desired infrastructure state, and Terraform provisions the resources accordingly.


## The folder structure promotes modularity and reusability:
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

4. 
## Verification: 
After successful deployment, use the provided endpoint URL (lambda_api_endpoint) to test the API functionality. This URL points to the specific Lambda function that retrieves data from S3.

you can use this url end point : lambda_api_endpoint = ** "https://mmt73opuqa.execute-api.eu-north-1.amazonaws.com/dev/retrieve_most_recent_object_dev" ** fet the latest s3 object

### Important Note:
The provided endpoint URL is specific to the development environment of this project and might not be publicly accessible.


# In Conclusion

This detailed breakdown of the README.md provides a comprehensive understanding of the serverless infrastructure project on AWS. By leveraging serverless components and Terraform for infrastructure management, the project offers scalability, cost-efficiency, and faster development cycles. If you're tasked with managing this project, ensure you have the required AWS credentials and Terraform installed to proceed with deployments.


