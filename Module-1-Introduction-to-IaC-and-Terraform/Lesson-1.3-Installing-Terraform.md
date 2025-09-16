# Lesson 1.3: Installing Terraform and Setting up the Environment

## Theory

Terraform is a cross-platform tool that can be installed on Windows, Mac, and Linux. It is distributed as a single binary executable. Setting up a proper development environment (IDE and CLI) is crucial for productivity and best practices.

**Installation Steps:**
- **Windows:** Download the zip from the official Terraform website, extract, and add the folder to your PATH.
- **Mac:** Use Homebrew: `brew tap hashicorp/tap && brew install hashicorp/tap/terraform`
- **Linux:** Download the binary, unzip, and move it to `/usr/local/bin`.

**Setting up IDE:**
- Recommended: Visual Studio Code with the HashiCorp Terraform extension for syntax highlighting, linting, and autocompletion.
- Alternative: IntelliJ IDEA with the Terraform plugin.

**Terraform CLI:**
- The CLI is used to initialize, plan, apply, and destroy infrastructure.

**Initializing a Terraform Project:**
- Create a directory for your project.
- Add a `main.tf` file with your configuration.
- Run `terraform init` to initialize the working directory and download required providers.

## Practical Example

**Install Terraform on Linux:**
```bash
wget https://releases.hashicorp.com/terraform/1.8.0/terraform_1.8.0_linux_amd64.zip
unzip terraform_1.8.0_linux_amd64.zip
sudo mv terraform /usr/local/bin/
terraform -version
```

**Set up a new project:**
```bash
mkdir terraform-demo
cd terraform-demo
echo 'terraform {
	required_providers {
		aws = {
			source = "hashicorp/aws"
			version = ">= 4.0"
		}
	}
}
' > main.tf
terraform init
```

## Real Case Scenario

**Scenario:**
An enterprise wants to standardize Terraform usage across teams and platforms.

**Solution:**
They create a setup guide for all developers, including OS-specific installation steps and recommended VS Code extensions. They also provide a project template with pre-configured provider blocks and a `terraform init` script.

**Outcome:**
- Faster onboarding for new team members.
- Consistent development environments.
- Fewer setup-related issues and support requests.

---
