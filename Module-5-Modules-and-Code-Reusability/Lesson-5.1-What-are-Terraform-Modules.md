# Lesson 5.1: What are Terraform Modules?

## Theory

**Modules** are containers for multiple resources that are used together. A module can be local (within your repo) or remote (from the Terraform Registry or a Git repo). Modules enable code reuse, organization, and sharing.

**Benefits:**
- DRY (Don't Repeat Yourself) principle
- Easier maintenance and updates
- Standardization across projects

## Practical Example

**Create and use a local module:**
1. Create a folder `modules/vpc` with a `main.tf` that defines a VPC resource.
2. In your root configuration:
```hcl
module "vpc" {
	source = "./modules/vpc"
	cidr_block = "10.0.0.0/16"
}
```
## More Module Examples

## Example: AWS EC2 Instance Module
Create a folder `modules/ec2` with a `main.tf` that defines an EC2 resource.
```hcl
resource "aws_instance" "example" {
	ami           = var.ami
	instance_type = var.instance_type
}
```
In your root configuration:
```hcl
module "ec2" {
	source        = "./modules/ec2"
	ami           = "ami-12345678"
	instance_type = "t2.micro"
}
```

## Example: Azure Storage Account Module
Create a folder `modules/storage_account` with a `main.tf` that defines a storage account resource.
```hcl
resource "azurerm_storage_account" "example" {
	name                     = var.name
	resource_group_name      = var.resource_group_name
	location                 = var.location
	account_tier             = "Standard"
	account_replication_type = "LRS"
}
```
In your root configuration:
```hcl
module "storage_account" {
	source              = "./modules/storage_account"
	name                = "examplestorageacct"
	resource_group_name = "example-rg"
	location            = "East US"
}
```

## Example: GCP Network Module
Create a folder `modules/network` with a `main.tf` that defines a VPC network resource.
```hcl
resource "google_compute_network" "vpc_network" {
	name                    = var.network_name
	auto_create_subnetworks = true
}
```
In your root configuration:
```hcl
module "network" {
	source       = "./modules/network"
	network_name = "example-network"
}
```

## Real Case Scenario

**Scenario:**
A cloud consultancy manages dozens of client projects, each needing a similar VPC setup.

**Solution:**
They create a reusable VPC module and use it in all client projects, customizing only the input variables.

**Outcome:**
- Faster project delivery.
- Fewer errors and inconsistencies.
- Easier updates and bug fixes across all clients.

---
