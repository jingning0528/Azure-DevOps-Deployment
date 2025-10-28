## 1. RBAC (Role-Based Access Control)

- When accessing Azure Cosmos DB from a VM, you may get a “Forbidden” error. This means that the **Managed Identity (Principal ID)** does not have the correct Cosmos DB role assignment.

```jsx
Code: Forbidden
Message: Request blocked by Auth cosmos : Request is blocked because principal [XXXXXXX] does not have required RBAC permissions to perform action
```

## 2. Retrieve the VM’s Managed Identity (Principal ID)

```jsx
az vm show \
  --name <VM_NAME> \
  --resource-group <RESOURCE_GROUP> \
  --query identity.principalId \
  -o tsv
```

## 3. Assign a Cosmos DB Role to the VM

- Use Azure CLI to assign a role that grants the VM access to Cosmos DB:

```jsx
az cosmosdb sql role assignment create \
  --account-name <COSMOS_DB_ACCOUNT_NAME> \
  --resource-group <RESOURCE_GROUP> \
  --principal-id <MANAGED_IDENTITY_OBJECT_ID> \
  --role-definition-id /subscriptions/<SUBSCRIPTION_ID>/resourceGroups/<RESOURCE_GROUP>/providers/Microsoft.DocumentDB/databaseAccounts/<COSMOS_DB_ACCOUNT_NAME>/sqlRoleDefinitions/00000000-0000-0000-0000-000000000002 \
  --scope "/"
```

- The role definition ID ‘00000000-0000-0000-0000-000000000002’ (Data Contributor) need MFA Authentication.

```jsx
az logout
az login --tenant "<TENANT ID>" --scope "https://graph.microsoft.com//.default"
```

## 4. Alternative: Assign Roles via Azure Portal Access control (IAM)

You can also assign RBAC roles through the Azure Portal:

→ Azure Portal → Cosmos DB → Access Control (IAM) → Add role assignment→ Select Role → Choose Managed identity → Assign

- However, **some built-in data roles** are **not visible** in the portal and must be assigned via **CLI** instead:
    - **Data Reader**: `00000000-0000-0000-0000-000000000001`
    - **Data Contributor**: `00000000-0000-0000-0000-000000000002`
