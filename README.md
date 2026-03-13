# Terraform AWS Modules

A collection of Terraform modules for deploying and managing AWS infrastructure components.

## Modules

This repository contains the following AWS Terraform modules:

### [ECS](./aws/ecs/)
Amazon Elastic Container Service (ECS) module for creating and managing ECS clusters, services, and tasks. Supports both EC2 and Fargate capacity providers, service discovery, and various deployment configurations.

### [EKS](./aws/eks/)
Amazon Elastic Kubernetes Service (EKS) module for provisioning and managing EKS clusters. Includes support for managed node groups, Fargate profiles, and various add-ons.

### [VPC](./aws/vpc/)
Amazon Virtual Private Cloud (VPC) module for creating VPCs with subnets, internet gateways, NAT gateways, security groups, and network ACLs. Supports IPv4 and IPv6 configurations.

## Usage

Each module can be used independently. Refer to the individual module's README for detailed usage instructions, input variables, and examples.

### Example

```hcl
module "vpc" {
  source  = "./aws/vpc"
  version = "~> 5.0"

  name = "my-vpc"
  cidr = "10.0.0.0/16"

  azs             = ["eu-west-1a", "eu-west-1b", "eu-west-1c"]
  private_subnets = ["10.0.1.0/24", "10.0.2.0/24", "10.0.3.0/24"]
  public_subnets  = ["10.0.101.0/24", "10.0.102.0/24", "10.0.103.0/24"]

  enable_nat_gateway = true
  enable_vpn_gateway = false

  tags = {
    Terraform = "true"
    Environment = "dev"
  }
}
```

## Requirements

- [Terraform](https://www.terraform.io/downloads.html) >= 1.0
- [AWS Provider](https://registry.terraform.io/providers/hashicorp/aws/latest) >= 6.28

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
