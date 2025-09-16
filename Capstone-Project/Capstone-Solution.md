# Capstone Project Solution: Step-by-Step Implementation

## 1. Set up Azure Provider and Backend
```hcl
provider "azurerm" {
  features {}
}

terraform {
  backend "azurerm" {
    resource_group_name  = "tfstate-rg"
    storage_account_name = "tfstateaccount"
    container_name       = "tfstate"
    key                  = "capstone.terraform.tfstate"
  }
}
```

## 2. Create Virtual Network (VNet), Subnets, Route Tables, and Security Groups
```hcl
resource "azurerm_resource_group" "main" {
  name     = "capstone-rg"
  location = "East US"
}

resource "azurerm_virtual_network" "main" {
  name                = "capstone-vnet"
  address_space       = ["10.0.0.0/16"]
  location            = azurerm_resource_group.main.location
  resource_group_name = azurerm_resource_group.main.name
}

resource "azurerm_subnet" "web" {
  name                 = "web-subnet"
  resource_group_name  = azurerm_resource_group.main.name
  virtual_network_name = azurerm_virtual_network.main.name
  address_prefixes     = ["10.0.1.0/24"]
}

resource "azurerm_network_security_group" "web" {
  name                = "web-nsg"
  location            = azurerm_resource_group.main.location
  resource_group_name = azurerm_resource_group.main.name
}
```

## 3. Provision Azure VMs with Load Balancer and Autoscaling
```hcl
resource "azurerm_linux_virtual_machine_scale_set" "web" {
  name                = "web-vmss"
  resource_group_name = azurerm_resource_group.main.name
  location            = azurerm_resource_group.main.location
  sku                 = "Standard_B1s"
  instances           = 2
  admin_username      = "azureuser"
  admin_password      = "P@ssword1234!"
  source_image_reference {
    publisher = "Canonical"
    offer     = "UbuntuServer"
    sku       = "18.04-LTS"
    version   = "latest"
  }
  network_interface {
    name    = "web-nic"
    primary = true
    subnet_id = azurerm_subnet.web.id
    network_security_group_id = azurerm_network_security_group.web.id
  }
}
```

## 4. Deploy Azure Storage Account, SQL Database, and Function App
```hcl
resource "azurerm_storage_account" "main" {
  name                     = "capstonestorage${random_id.unique.hex}"
  resource_group_name      = azurerm_resource_group.main.name
  location                 = azurerm_resource_group.main.location
  account_tier             = "Standard"
  account_replication_type = "LRS"
}

resource "azurerm_sql_server" "main" {
  name                         = "capstonesqlserver${random_id.unique.hex}"
  resource_group_name          = azurerm_resource_group.main.name
  location                     = azurerm_resource_group.main.location
  version                      = "12.0"
  administrator_login          = "sqladminuser"
  administrator_login_password = "P@ssword1234!"
}

resource "azurerm_sql_database" "main" {
  name                = "capstonedb"
  resource_group_name = azurerm_resource_group.main.name
  location            = azurerm_resource_group.main.location
  server_name         = azurerm_sql_server.main.name
  requested_service_objective_name = "S0"
}

resource "azurerm_storage_account" "function" {
  name                     = "capstonefunc${random_id.unique.hex}"
  resource_group_name      = azurerm_resource_group.main.name
  location                 = azurerm_resource_group.main.location
  account_tier             = "Standard"
  account_replication_type = "LRS"
}

resource "azurerm_function_app" "main" {
  name                       = "capstone-func-app"
  location                   = azurerm_resource_group.main.location
  resource_group_name        = azurerm_resource_group.main.name
  app_service_plan_id        = azurerm_app_service_plan.main.id
  storage_account_name       = azurerm_storage_account.function.name
  storage_account_access_key = azurerm_storage_account.function.primary_access_key
  version                    = "~4"
}
```

## 5. Configure Remote State and Version Control
- The backend block above stores state in Azure Storage.
- Use Git for version control and collaboration.

## 6. Integrate with CI/CD Pipeline
- Use GitHub Actions or Azure DevOps to run `terraform init`, `plan`, and `apply` on PR merge.
- Store secrets in repository or pipeline secrets.

## 7. Clean Up
- Run `terraform destroy` to remove all resources when finished.

---

> **Note:** This is a simplified solution. In production, use modules, variables, outputs, and secure secrets management. Adjust resource names and regions as needed.
