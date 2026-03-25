Terraform for azure
🧱 What we’re setting up

We’ll configure Terraform to:

Authenticate with Azure
Use the Azure provider
Create a basic resource (like a Storage Account)

⚙️ Step 1: Install prerequisites

Make sure you have:

Terraform
Azure CLI → Azure CLI
terraform -v
az version

Step 2 login to azure
az login
If you have multiple subscriptions:
az account set --subscription "YOUR_SUBSCRIPTION_NAME"

Step 3: Create project structure
mkdir terraform-azure
cd terraform-azure
touch main.tf

Step 4: Write Terraform config

Here’s a minimal working config:
provider "azurerm" {
  features {}
}

resource "azurerm_resource_group" "rg" {
  name     = "rg-demo-terraform"
  location = "Central India"
}

resource "azurerm_storage_account" "sa" {
  name                     = "jayeshstorage123" # must be globally unique
  resource_group_name      = azurerm_resource_group.rg.name
  location                 = azurerm_resource_group.rg.location
  account_tier             = "Standard"
  account_replication_type = "LRS"
}

Step 5: Initialize Terraform then plan and apply
terraform init
terraform plan
terraform apply 

when you are done with this you can destroy all the terraform reasources using
terraform destroy
