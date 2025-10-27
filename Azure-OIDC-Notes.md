Based on repository: bcgov/quickstart-azure-containers: Quickstart for Azure using Azure Postgresql, Azure App Service, and Azure Front Door 

### Issue 1: Azure CLI cannot be installed locally. 
Problem: Azure CLI could not be installed or used on the local machine.
Fixed: Use the Azure Cloud Shell directly from the Azure Portal instead of installing CLI locally.

### Issue 2: Azure CLI cannot find the resource group.
Fix Steps:
```
az account list –-output table
az account set --subscription "subscription name"
az group list --output table
```
Confirms the correct subscription and resource group are selected.

### Issue 3: GitHub CLI Login
Steps to Authenticate:
```
gh auth login
```
Then choose: 
-> Github.com
-> HTTPS
-> Paste an authentication token

### Issue 4: Azure Account Authorization
Error Message: 
```
Login failed with Error: Using auth-type: SERVICE_PRINCIPAL.
Not all values are present.
Ensure 'client-id' and 'tenant-id' are supplied. Double check if the 'auth-type' is correct.
```

Fix: Ensure Azure account has Owner/Contributer permissions.

Reference: 
- https://github.com/Azure/login#readme
- https://learn.microsoft.com/en-us/answers/questions/1685245/receiving-login-failed-with-error-using-auth-type

### Issue 5: Missing Environment Configuration
Problem: Workflow fails due to missing environment context in GitHub Actions.
Fix: Add an environment name (e.g., dev) in the workflow YAML:
```
jobs:
  test-login:
    runs-on: ubuntu-latest
    environment: <dev>
    steps:
      - name: Azure Login via OIDC
        uses: azure/login@v2
```

### Issue 6: Missing Deployment Permissions
Problem: Managed identity does not have sufficient access to deploy resources.

Fis Steps:

1. Go to Azure Portal → Managed Identities

2. Select your managed identity

3. Copy the Object ID

4. Navigate to Microsoft Entra ID → Groups

5. Open the target security group

6. Click Add Members → Paste Object ID → Select

