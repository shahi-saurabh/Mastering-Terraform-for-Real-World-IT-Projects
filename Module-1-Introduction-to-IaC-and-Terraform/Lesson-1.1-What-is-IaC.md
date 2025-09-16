
# Lesson 1.1: What is Infrastructure as Code (IaC)?

## Theory

**Definition:**
Infrastructure as Code (IaC) is the process of managing and provisioning computing infrastructure (networks, virtual machines, load balancers, and connection topology) through machine-readable definition files, rather than physical hardware configuration or interactive configuration tools.

**Benefits:**
- **Consistency:** Ensures the same environment is provisioned every time.
- **Speed:** Automates infrastructure provisioning, reducing manual effort.
- **Version Control:** Infrastructure definitions can be versioned and tracked in source control systems like Git.
- **Collaboration:** Teams can collaborate on infrastructure changes using code review and pull requests.
- **Disaster Recovery:** Infrastructure can be quickly rebuilt from code in case of failure.

**IaC vs Traditional Infrastructure Management:**
- Traditional: Manual setup, error-prone, hard to reproduce.
- IaC: Automated, repeatable, and reliable.

**Tools Comparison:**
- **Terraform:** Cloud-agnostic, declarative, supports many providers.
- **CloudFormation:** AWS-specific, declarative.
- **Ansible:** Procedural, configuration management, supports many platforms.
- **Puppet:** Procedural, configuration management, agent-based.

## Practical Example

Suppose you want to provision an AWS EC2 instance manually:
- You would log in to the AWS console, click through several screens, and configure the instance by hand.
- This process is slow, error-prone, and hard to repeat.

With IaC (using Terraform):
```hcl
resource "aws_instance" "example" {
	ami           = "ami-0c55b159cbfafe1f0"
	instance_type = "t2.micro"
}
```
- Save this code in a file (e.g., `main.tf`), run `terraform init` and `terraform apply`.
- The EC2 instance is provisioned automatically, and the process can be repeated or shared with others.

## Real Case Scenario

**Scenario:**
A fintech company needs to deploy identical environments for development, testing, and production. Manual setup led to inconsistencies and bugs that only appeared in production.

**Solution:**
The company adopted IaC with Terraform. All environments are now defined in code, stored in Git, and deployed automatically. This eliminated environment drift, reduced deployment time from days to minutes, and improved reliability.

**Outcome:**
- Faster onboarding for new developers.
- Easier disaster recovery.
- Improved collaboration between DevOps and development teams.

---
