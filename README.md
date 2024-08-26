# AWS Three-Tier Architecture Deployment #
This repository contains the code and configuration files to deploy a fully automated AWS three-tier architecture, including VPC setup, database deployment, application tier, and load balancing.

## Table of Contents

1. Architecture Overview 
2.  AWS Services Used
3. Medium Article
4. Prerequisites
5. Deployment Steps
6. Project Structure
7. Accessing the Application
8. Cleanup
   
### 1. Architecture Overview
  ![Architecture Diagram](https://github.com/Naimat250/aws-three-tier-web-architecture-workshop/blob/78e3ec9a12cad699f0884bb3f304c84f8beba355/Architecture.PNG)

This project sets up a three-tier architecture on AWS, including:

1. Web Tier: Handles incoming traffic through an external Application Load Balancer (ALB).
2. App Tier: Processes business logic, connects to the database, and scales based on demand using Auto Scaling Groups (ASG) and an internal ALB.
3. Database Tier: Uses AWS Aurora for data storage, accessible only from the private subnet.
### 2. AWS Services Used
1. Amazon VPC: For creating isolated networks.
2. Amazon EC2: For deploying instances in different tiers.
3. Amazon RDS (Aurora): For the database layer.
4. Elastic Load Balancing (ALB): For distributing traffic across instances.
5. Auto Scaling Groups (ASG): For scaling instances based on demand.
6. Amazon S3: For storing application files.

### 3. Medium Article
For a detailed explanation of the project, check out the Medium article: [ [Deploying a Three-Tier Web App on AWS](https://medium.com/@niamatu250/deploying-a-three-tier-web-app-on-aws-ac8bf9f47a11)].

### 4. Prerequisites
Before deploying this architecture, ensure you have the following:

1. An AWS account with sufficient permissions.
2. AWS CLI configured with the necessary credentials.
3. IAM roles with the following permissions:
  - AmazonSSMManagedInstanceCore
  - AmazonS3ReadOnlyAccess

### 5. Deployment Steps
- Clone the Repository
- Create S3 Bucket
  - Set up an S3 bucket to store your application files and assets. 
- IAM EC2 Instance Role Creation
  - Create an IAM role with AmazonSSMManagedInstanceCore and AmazonS3ReadOnlyAccess permissions.
- VPC and Subnets Setup
    - Create a VPC, subnets, and configure routing and security groups.
- Database and Subnet Group Deployment
    - Deploy an AWS Aurora database and create a subnet group for the database.
- App Tier Instance Deployment and DB Configuration
    - Launch and configure EC2 instances for the app tier, and update the database connection in your application.
- ALB and ASG for App Tier
    - Set up an internal ALB and configure an Auto Scaling Group for your app tier.
- Web Tier Instance Deployment
    - Launch and configure EC2 instances for the web tier, including setting up security groups.
- External ALB and ASG Configuration
    - Set up an external ALB for incoming traffic and configure an Auto Scaling Group for the web tier.
- Access the Application
    - Access the application via the DNS of the external ALB.
- Cleanup

Don’t forget to delete all AWS resources used in the deployment to avoid unnecessary charges.

### 6. Project Structure
  ![Project Structure](https://github.com/Naimat250/aws-three-tier-web-architecture-workshop/blob/8f0c9463866110b57c5408b95a3ddbebb81f8aa8/project-structure.PNG)

### 7. Accessing the Application
Once deployed, your application will be accessible via the DNS name of the external ALB. Verify that your setup is complete and the application is functioning as expected.

### 8. Cleanup 
To avoid incurring charges, ensure that you delete all AWS resources provisioned during this deployment, including EC2 instances, ALBs, VPC and S3 buckets.
