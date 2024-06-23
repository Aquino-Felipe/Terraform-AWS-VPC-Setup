# Terraform AWS VPC Setup

This repository contains the Terraform configuration files to set up a VPC with multiple subnets, an Internet Gateway, a NAT Gateway, and associated route tables in AWS.

## Components

### VPC
- **VPC**: `VPC (demo_environment)`

### Subnets
- **Public Subnets**:
  - `public_subnet_1`
  - `public_subnet_2`
  - `public_subnet_3`
- **Private Subnets**:
  - `private_subnet_1`
  - `private_subnet_2`
  - `private_subnet_3`

### Internet Gateway
- **Internet Gateway**: `Internet Gateway (demo_igw)`

### NAT Gateway
- **NAT Gateway**: `NAT Gateway (demo_nat_gateway)`

### EIP
- **Elastic IP (EIP)**: `EIP (demo_igw_eip)`

### Route Tables
- **Public Route Table**: `Public Route Table (demo_public_rtb)`
- **Private Route Table**: `Private Route Table (demo_private_rtb)`

## Prerequisites

- [Terraform](https://www.terraform.io/downloads.html) installed on your local machine.
- AWS CLI installed and configured with your AWS credentials.

## Files

- `main.tf`: Contains the main Terraform configuration.
- `variables.tf`: Contains the variable definitions for the Terraform configuration.

## Setup

### Task 8: Set Credentials for Terraform Deployment

#### Step 8.1
Now that we have our Terraform files ready to go, the last step we need to complete is setting a few environment variables to set our AWS credentials and region used by Terraform. In AWS, generate an access key and secret key from an IAM user with Administrative privileges. If you need help, check out this [link](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html) with a walk-through.

Once you have credentials, set the following environment variables for Linux, MacOS, or Bash on Windows:
```sh
export AWS_ACCESS_KEY_ID="<YOUR ACCESS KEY>"
export AWS_SECRET_ACCESS_KEY="<YOUR SECRET KEY>"
