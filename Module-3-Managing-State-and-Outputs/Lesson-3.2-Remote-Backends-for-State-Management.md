# Lesson 3.2: Remote Backends for State Management

## Theory

**Remote Backends:**
Remote backends store Terraform state files in a central, remote location, enabling collaboration, state locking, and versioning. Common backends include AWS S3, Azure Blob Storage, and Google Cloud Storage.

**Locking and Versioning:**
- **Locking:** Prevents concurrent modifications to state files, reducing the risk of corruption.
- **Versioning:** Maintains a history of state changes for rollback and auditing.

**Security and Access:**
- Use IAM roles, access policies, and encryption to secure state files.
- Limit access to only those who need it.

## Practical Example

**Configure S3 backend for remote state:**
```hcl
terraform {
	backend "s3" {
		bucket         = "my-terraform-state-bucket"
		key            = "global/s3/terraform.tfstate"
		region         = "us-east-1"
		dynamodb_table = "terraform-lock"
		encrypt        = true
	}
}
```

**Steps:**
1. Create the S3 bucket and DynamoDB table for locking.
2. Add the backend block to your configuration.
3. Run `terraform init` to migrate state.

## Real Case Scenario

**Scenario:**
A global company needs to ensure only one person can modify infrastructure at a time and that all changes are auditable.

**Solution:**
They use S3 for state storage and DynamoDB for state locking, with versioning enabled on the S3 bucket.

**Outcome:**
- Safe, auditable, and collaborative infrastructure management.
- Reduced risk of state file conflicts.
- Easy rollback to previous states.

---
