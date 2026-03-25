# 🚀 Terraform Setup for Azure

## 🧱 What we’re setting up

We’ll configure Terraform to:

* Authenticate with Azure
* Use the Azure provider
* Create a basic resource (Storage Account)

---

## ⚙️ Step 1: Install prerequisites

Make sure you have:

* Terraform
* Azure CLI

Check versions:

```bash
terraform -v
az version
```

---

## 🔐 Step 2: Login to Azure

```bash
az login
```

If you have multiple subscriptions:

```bash
az account set --subscription "YOUR_SUBSCRIPTION_NAME"
```

---

## 📁 Step 3: Create project structure

```bash
mkdir terraform-azure
cd terraform-azure
touch main.tf
```

---

## 🧩 Step 4: Write Terraform config

Paste this into `main.tf`:

```hcl
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
```

---

## 🚀 Step 5: Initialize, Plan, Apply

```bash
terraform init
terraform plan
terraform apply
```

---

## 🧹 Cleanup (Destroy resources)

```bash
terraform destroy
```
