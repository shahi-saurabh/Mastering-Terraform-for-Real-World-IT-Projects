# Module 6 Quiz

1. What is an implicit dependency in Terraform?
2. How do you create an explicit dependency?
3. What are workspaces used for?
4. Give an example of a provisioner in Terraform.

## Answer Key
1. When one resource references another, creating a dependency automatically.
2. Using the `depends_on` argument.
3. Managing multiple environments with separate state files.
4. remote-exec, local-exec, etc.
