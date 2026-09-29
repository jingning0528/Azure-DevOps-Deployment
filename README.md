# Azure Deployment Notes & Troubleshooting

A practical collection of deployment notes for working with Azure, GitHub Actions, managed identities, and role-based access control (RBAC).

These guides capture common setup steps and solutions to issues encountered while deploying Azure resources.

## Guides

| Guide | What it covers |
| --- | --- |
| [OIDC Deployment](OIDC%20Deployment.md) | GitHub Actions authentication with Azure OIDC, subscription setup, environment configuration, and deployment permissions |
| [Virtual Machine Deployment](Virtual%20Machine%20Deployment.md) | Secure VM configuration, Bastion access, essential tools, Azure CLI sign-in, and MFA |
| [Cosmos DB Deployment](Cosmos%20DB%20Deployment.md) | Managed identity access, Cosmos DB RBAC, and Data Reader or Data Contributor role assignments |

## Prerequisites

- An Azure subscription and permission to manage the relevant resources
- Access to the Azure Portal or Azure Cloud Shell
- A GitHub account for workflows that use GitHub Actions
- Familiarity with Azure CLI commands

## How to Use This Repository

Choose the guide that matches your deployment task, then replace placeholders such as `<RESOURCE_GROUP>`, `<VM_NAME>`, and `<SUBSCRIPTION_ID>` with values from your Azure environment.

> [!IMPORTANT]
> Review commands and role assignments before running them. Use least-privilege access, and never commit passwords, tokens, tenant secrets, or other credentials to the repository.

## Reference Project

The OIDC notes reference the [`bcgov/quickstart-azure-containers`](https://github.com/bcgov/quickstart-azure-containers) project.
