# Lesson 2.3: Managing Providers and Resources

## Theory

**Configuring Multiple Providers:**
Terraform allows you to use multiple providers in a single configuration, enabling multi-cloud or hybrid deployments. Providers can be aliased for use in different regions or accounts.

**Provider Configuration and Versioning:**
- Specify provider versions in the `required_providers` block to ensure consistent environments.
- Use provider aliases for multiple configurations.

**Managing Resource Lifecycle:**
- **Create:** Resources are created when not present.
- **Update:** Changes in configuration are applied to existing resources.
- **Delete:** Resources are destroyed when removed from configuration or with `terraform destroy`.

## Practical Example

**Configure two AWS providers for different regions:**
```hcl
provider "aws" {
	region = "us-east-1"
}

provider "aws" {
	alias  = "west"
	region = "us-west-2"
}

resource "aws_instance" "east" {
	ami           = "ami-0c55b159cbfafe1f0"
	instance_type = "t2.micro"
}

resource "aws_instance" "west" {
	provider      = aws.west
	ami           = "ami-0c55b159cbfafe1f0"
	instance_type = "t2.micro"
}
```

## Real Case Scenario

**Scenario:**
An e-commerce company needs to deploy resources in multiple AWS regions for high availability.

**Solution:**
They use provider aliases to manage resources in both `us-east-1` and `us-west-2`, ensuring redundancy and failover capability.

**Outcome:**
- Improved uptime and disaster recovery.
- Centralized management of multi-region infrastructure.
- Simplified scaling and updates.

---
