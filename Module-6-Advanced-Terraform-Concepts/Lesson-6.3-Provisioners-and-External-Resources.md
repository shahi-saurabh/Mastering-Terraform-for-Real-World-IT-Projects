# Lesson 6.3: Provisioners and External Resources

## Theory

**Provisioners** in Terraform allow you to execute scripts or commands on a local or remote machine after a resource is created. Use them sparingly, as they can introduce complexity and are not idempotent.

**External Resources:**
Terraform can manage resources outside of its direct control using the `external` data source or by integrating with other tools.

## Practical Example

**Use a remote-exec provisioner to install Nginx:**
```hcl
resource "aws_instance" "web" {
	ami           = "ami-0c55b159cbfafe1f0"
	instance_type = "t2.micro"

	provisioner "remote-exec" {
		inline = [
			"sudo apt-get update",
			"sudo apt-get install -y nginx"
		]
	}
}
```

**Use the external data source:**
```hcl
data "external" "example" {
	program = ["python3", "./scripts/get_data.py"]
}
```

## Real Case Scenario

**Scenario:**
A company needs to run a configuration script on every new server after creation.

**Solution:**
They use the `remote-exec` provisioner to automate post-deployment setup.

**Outcome:**
- Automated, consistent server configuration.
- Reduced manual intervention.
- Faster, more reliable deployments.

---
