# Lesson 2.2: Defining Resources

## Theory

**Resources** are the fundamental building blocks in Terraform. Each resource block describes one or more infrastructure objects, such as virtual machines, storage accounts, or networking components.

**Resource Attributes and Arguments:**
- **Attributes:** Properties of the resource (e.g., `id`, `arn`, `public_ip`).
- **Arguments:** Configuration options you set (e.g., `instance_type`, `ami`).

**Referencing Resources:**
You can reference the attributes of one resource in another using interpolation syntax: `resource_type.resource_name.attribute`.

## Practical Example

**Define an AWS EC2 instance and reference its public IP:**
```hcl
resource "aws_instance" "web" {
	ami           = "ami-0c55b159cbfafe1f0"
	instance_type = "t2.micro"
}

output "instance_ip" {
	value = aws_instance.web.public_ip
}
```

## Real Case Scenario

**Scenario:**
A SaaS company needs to provision a database and connect it to a web server, ensuring the web server knows the database endpoint.

**Solution:**
They define both resources in Terraform and use outputs and references to pass the database endpoint to the web server configuration.

**Outcome:**
- Automated, error-free resource connections.
- Easier scaling and updates.
- Improved infrastructure reliability.

---
