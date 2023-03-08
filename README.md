
# Create a Jenkins Server on AWS with Terraform

## AWS Resources covered in this setup
- VPC
- Public Subnet
- EC2 Key pair
- EC2
- Security Group
- Elastic IP

## Setup Terraform 
- If you don't have Terraform set up on your machine(Local or ec2) please follow this link to configure
[Download Terraform](https://www.terraform.io/downloads.html)
[Configure Terraform](https://learn.hashicorp.com/tutorials/terraform/install-cli)

## Setup Terraform user profile
- Open `provider.tf`
- Add the AWS-CLI profile name.

provider "aws" {
  region  = "${var.region}"
  profile = "<AWS-CLI PROFILE NAME>" //If you run this script using AWS EC2
}


## terraform.tfvrs file variables
- aws_region = Terraform create all resources in a given region (ap-southeast-1)
- vpc_cidr_block           = VPC CIDR ranger
- public_subnet_cidr_block = Public subnet CIDR ranger
- my_ip                    = Your machine's IP

## Create a Key Pair
`ssh-keygen -t rsa -b 4096 -m pem -f aws_rp && mv aws_rp.pub modules/compute/aws_rp.pub && mv aws_rp aws_rp.pem && chmod 400 aws_rp.pem`

## Run Terraform
- Initialize terrafom: `terraform init`
- Run: `terraform apply"`

## To destroy everything Terraform built
`terraform destroy"`

