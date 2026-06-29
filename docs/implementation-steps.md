# Implementation Steps

This guide explains how someone can follow the project pattern and understand the steps used to build and push secure artifacts to Azure Container Registry with GitHub Actions.

## Step 1: Create an Azure Container Registry

Create an ACR instance in Azure.

Example command:

```bash
az acr create \
  --resource-group <resource-group-name> \
  --name <acr-name> \
  --sku Basic
```

## Step 2: Confirm the Registry Exists

```bash
az acr show \
  --name <acr-name> \
  --resource-group <resource-group-name> \
  --output table
```

## Step 3: Create Azure Credentials for GitHub Actions

Create a service principal or federated identity that GitHub Actions can use to authenticate to Azure.

The recommended production pattern is OpenID Connect because it avoids long-lived secrets.

For lab purposes, many people use an `AZURE_CREDENTIALS` secret.

## Step 4: Add GitHub Repository Secrets

In GitHub, go to:

```text
Repository → Settings → Secrets and variables → Actions → New repository secret
```

Add values such as:

```text
AZURE_CREDENTIALS
ACR_NAME
ACR_LOGIN_SERVER
AZURE_RESOURCE_GROUP
AZURE_SUBSCRIPTION_ID
```

## Step 5: Create the GitHub Actions Workflow

Create a workflow file under:

```text
.github/workflows/
```

The workflow should:

1. Check out the repository
2. Authenticate to Azure
3. Build the container artifact
4. Tag the artifact
5. Push the image to Azure Container Registry

## Step 6: Build the Artifact

The workflow builds the container image from the repository.

A common tagging pattern is:

```text
<acr-login-server>/<image-name>:<github-sha>
```

This keeps each build traceable back to a GitHub commit.

## Step 7: Push the Artifact to ACR

The image is pushed into Azure Container Registry.

After that, the artifact becomes available for future deployment into AKS or another Azure runtime.

## Step 8: Validate the Artifact

List repositories in ACR:

```bash
az acr repository list \
  --name <acr-name> \
  --output table
```

Show tags for an image repository:

```bash
az acr repository show-tags \
  --name <acr-name> \
  --repository <repository-name> \
  --output table
```

## Step 9: Connect to Future Deployment Work

Once the artifact exists in ACR, the next phase could be deploying it to:

- Azure Kubernetes Service
- Azure App Service for Containers
- Azure Container Apps
- A private AKS platform pipeline

## Expected Outcome

At the end of this project, a user should be able to explain:

- How GitHub Actions can automate build tasks
- Why ACR is used as a trusted container registry
- How artifacts become traceable through tagging
- Why this pattern matters before deploying into AKS
- How this supports cloud engineering and platform engineering workflows
