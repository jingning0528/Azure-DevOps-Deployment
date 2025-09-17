Based on repository: bcgov/quickstart-azure-containers: Quickstart for Azure using Azure Postgresql, Azure App Service, and Azure Front Door 

### Issue 1: Azure CLI cannot be installed locally. 
Fixed: Use Azure portal cloud shell.
### Issue 2: Cannot find the resource group.
Fixed:
```
az account list –-output table
az account set --subscription "subscription name"
az group list --output table
```
### Issue 3: GitHub CLI Login
```
gh auth login
```
-> Github.com
-> HTTPS
-> Paste an authentication token

### Issue 4: Security Group

### Issue 5: Environment
