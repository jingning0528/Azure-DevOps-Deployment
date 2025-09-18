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

### Issue 4: Azure Account Authorization
Error: Login failed with Error: Using auth-type: SERVICE_PRINCIPAL. Not all values are present. Ensure 'client-id' and 'tenant-id' are supplied.. Double check if the 'auth-type' is correct. Refer to https://github.com/Azure/login#readme for more information.

Fixed: Azure account set to Owner/Contributer
Reference: https://learn.microsoft.com/en-us/answers/questions/1685245/receiving-login-failed-with-error-using-auth-type

### Issue 5: Environment
Fixed: Add `environment: <dev>`
```
jobs:
  test-login:
    runs-on: ubuntu-latest
    environment: <dev>
    steps:
      - name: Azure Login via OIDC
        uses: azure/login@v2
```

### Issue 6: Adds managed identity to security group for deployment permissions
- Azure Portal > Managed Identities.
- Select your identity ID
- Copy the Object ID
- Azure Portal > Microsoft Entra ID > Select Security Group Name
- Groups > Add Members > Paste Object ID > Select

### Issue 7: [WARNING] Security group 'xxx' does not exist.
