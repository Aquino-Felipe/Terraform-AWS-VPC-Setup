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

### Set Credentials for Terraform Deployment

```sh
export AWS_ACCESS_KEY_ID="<YOUR ACCESS KEY>"
export AWS_SECRET_ACCESS_KEY="<YOUR SECRET KEY>"
```


## Initialize Terraform
To begin using Terraform, you need to initialize the working directory. In your shell session, enter the following command:

```sh
terraform init
```
```sh
Initializing the backend...

Initializing provider plugins...
- Checking for available provider plugins...
- Downloading plugin for provider "aws" (hashicorp/aws) 3.37.0...

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.
```


## Plan Terraform Execution

With our working directory now initialized, we can generate an execution plan. This plan will offer a preview of the changes to our AWS environment. To generate the plan, run the following command:

```sh
terraform plan
```

![alt text](terraform-plan.png)

## Apply Terraform Configuration

As the final step to provision our AWS resources, we need to apply the configuration. Running this command will direct Terraform to create the resources in AWS as specified in our configuration files. To execute this, use the following command:

```sh
terraform apply -auto-approve
```
```sh
Please note, we are using the `-auto-approve` flag for convenience. You can omit this flag to manually review the changes and type yes to confirm the application of the configuration.

data.aws_region.current: Refreshing state...
data.aws_availability_zones.available: Refreshing state...

An execution plan has been generated and is shown below.
Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  # aws_eip.nat_gateway_eip will be created
  + resource "aws_eip" "nat_gateway_eip" {
      + allocation_id        = (known after apply)
      + association_id       = (known after apply)
      + carrier_ip           = (known after apply)
      + customer_owned_ip    = (known after apply)
      + domain               = (known after apply)
      + id                   = (known after apply)
      + instance             = (known after apply)
      + network_border_group = (known after apply)
      + network_interface    = (known after apply)
      + private_dns          = (known after apply)
      + private_ip           = (known after apply)
      + public_dns           = (known after apply)
      + public_ip            = (known after apply)
      + public_ipv4_pool     = (known after apply)
      + tags                 = {
          + "Name" = "demo_igw_eip"
        }
      + vpc                  = true
    }
...
aws_vpc.vpc: Creating...
aws_vpc.vpc: Still creating... [10s elapsed]
aws_vpc.vpc: Creation complete after 11s [id=vpc-05bf9e6a14d8ee736]
aws_subnet.private_subnets["private_subnet_2"]: Creating...
aws_subnet.public_subnets["public_subnet_3"]: Creating...
aws_internet_gateway.internet_gateway: Creating...
aws_subnet.public_subnets["public_subnet_1"]: Creating...
aws_subnet.private_subnets["private_subnet_1"]: Creating...
aws_subnet.public_subnets["public_subnet_2"]: Creating...
aws_subnet.private_subnets["private_subnet_3"]: Creating...
aws_subnet.private_subnets["private_subnet_3"]: Creation complete after 2s [id=subnet-097ce13a4cd397b92]
aws_subnet.private_subnets["private_subnet_2"]: Creation complete after 2s [id=subnet-0e13dbad1bdcc9b3d]
aws_internet_gateway.internet_gateway: Creation complete after 3s [id=igw-09460c69ff2efdaa7]
aws_eip.nat_gateway_eip: Creating...
aws_route_table.public_route_table: Creating...
aws_subnet.private_subnets["private_subnet_1"]: Creation complete after 3s [id=subnet-0cd287fb292ad3720]
aws_eip.nat_gateway_eip: Creation complete after 1s [id=eipalloc-0834ec4c7cb0ff0d1]
aws_route_table.public_route_table: Creation complete after 2s [id=rtb-0f354a5a7facfe6f1]
aws_subnet.public_subnets["public_subnet_1"]: Still creating... [10s elapsed]
aws_subnet.public_subnets["public_subnet_2"]: Still creating... [10s elapsed]
aws_subnet.public_subnets["public_subnet_3"]: Still creating... [10s elapsed]
aws_subnet.public_subnets["public_subnet_3"]: Creation complete after 13s [id=subnet-09b2418caea54512e]
aws_subnet.public_subnets["public_subnet_2"]: Creation complete after 14s [id=subnet-0fd89ea15770c4658]
aws_subnet.public_subnets["public_subnet_
```

## Delete the AWS resources using Terraform

The last step involves tearing down all the resources created by Terraform. Using Terraform to perform this destruction guarantees that all resources it deployed are removed from your account, preventing any unintended costs or leftover technical debt.

To remove your resources, run the following command in the terminal. Terraform will refresh the state of each resource and then destroy them in the correct sequence.

```sh
terraform destroy -auto-approve
```
![alt text](terraform-destroy.png)

## Conclusion
#### Congratulations! You have successfully set up a VPC with multiple subnets, an Internet Gateway, a NAT Gateway, and associated route tables using Terraform. This automated process ensures a consistent and repeatable infrastructure setup, making it easier to manage and scale your AWS resources. By following these steps, you have learned how to:

- #### Initialize a Terraform working directory.
- #### Plan and apply Terraform configurations.
- #### Set up necessary AWS resources through Terraform.
- #### Tear down the infrastructure to avoid unnecessary costs and manage resources effectively.

#### Feel free to explore the AWS console to see the resources you created, and leverage this setup for more complex infrastructure as needed. Happy Terraforming!
