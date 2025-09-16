# Lesson 3.3: Outputs and Data Sources

## Theory

**Outputs:**
Outputs allow you to display and export values from your Terraform configuration, such as resource attributes or computed values. They are useful for passing information to other modules or users.

**Data Sources:**
Data sources allow Terraform to fetch and use information defined outside your configuration (e.g., existing VPCs, AMIs, or secrets).

**Using Outputs in Other Resources:**
Outputs can be referenced in other modules or scripts, enabling integration and automation.

## Practical Example

**Output the public IP of an EC2 instance:**
```hcl
resource "aws_instance" "web" {
	ami           = "ami-0c55b159cbfafe1f0"
	instance_type = "t2.micro"
}

output "instance_ip" {
	value = aws_instance.web.public_ip
}
```

**Use a data source to fetch the latest AMI:**
```hcl
data "aws_ami" "latest" {
	most_recent = true
	owners      = ["amazon"]
	filter {
		name   = "name"
		values = ["amzn2-ami-hvm-*-x86_64-gp2"]
	}
}

resource "aws_instance" "web" {
	ami           = data.aws_ami.latest.id
	instance_type = "t2.micro"
}
```

## Real Case Scenario

**Scenario:**
A DevOps team needs to share the database endpoint with application developers after provisioning.

**Solution:**
They use an output block to display the endpoint after `terraform apply`, and a data source to fetch existing VPC information for new resources.

**Outcome:**
- Seamless handoff between infrastructure and application teams.
- Automated integration with existing resources.
- Reduced manual communication and errors.

---
