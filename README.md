# Build and Push Secure Artifacts to Azure Container Registry with GitHub Actions

## Project Overview

This project demonstrates how to build a secure and repeatable CI/CD workflow that packages an application artifact and pushes it to **Azure Container Registry (ACR)** using **GitHub Actions**.

The goal of this lab is to show how a cloud engineering or platform engineering team can move away from manual artifact handling and toward a cleaner, automated delivery foundation.

In a real cloud environment, teams need to know that the artifact being deployed is consistent, traceable, and stored in a trusted registry before it moves into AKS, App Service, or another Azure hosting platform.

## The Pain Point

Many teams struggle with manual or inconsistent build processes.

Common problems include:

- Developers building images differently on local machines
- Release artifacts being difficult to track
- Container images being pushed manually
- Limited visibility into what version was built and deployed
- No repeatable pipeline for preparing artifacts for cloud deployment

## The Solution

This project uses **GitHub Actions** to automate the artifact workflow and push the final image to **Azure Container Registry**.

The workflow creates a stronger cloud delivery foundation by making the process:

- Repeatable
- Traceable
- Easier to maintain
- Better aligned with DevOps and platform engineering practices
- Ready for downstream deployment into Azure services such as AKS

## Architecture Flow

```text
Developer pushes code to GitHub
        ↓
GitHub Actions workflow starts
        ↓
Application/container artifact is built
        ↓
Image is tagged/versioned
        ↓
Image is pushed to Azure Container Registry
        ↓
Artifact is ready for AKS or another Azure deployment target
```

## Technologies Used

- Azure Container Registry (ACR)
- GitHub Actions
- Docker / container artifacts
- Azure CLI
- CI/CD automation
- Cloud engineering fundamentals
- Platform engineering fundamentals

## What This Project Demonstrates

This repository demonstrates the ability to:

- Design a secure artifact workflow
- Automate cloud delivery tasks with GitHub Actions
- Push container images to Azure Container Registry
- Prepare container artifacts for AKS or other Azure services
- Think through cloud delivery from a platform engineering perspective
- Create repeatable cloud deployment foundations

## Why This Matters

Before an application can run reliably in AKS or any container-based environment, the team needs a trusted way to build and store its container artifacts.

This project focuses on that foundation.

It shows the first critical step in a cloud-native delivery workflow: securely building and storing the artifact before deployment.

## Prerequisites

Before running this lab, you should have:

- An Azure subscription
- An Azure Container Registry
- A GitHub repository
- GitHub Actions enabled
- Dockerfile or application artifact to build
- Azure credentials configured as GitHub repository secrets

## Required GitHub Secrets

Create the following secrets in your GitHub repository settings:

```text
AZURE_CREDENTIALS
ACR_NAME
ACR_LOGIN_SERVER
```

Depending on your workflow configuration, you may also need:

```text
AZURE_SUBSCRIPTION_ID
AZURE_RESOURCE_GROUP
```

## High-Level Steps

1. Create or identify an Azure Container Registry.
2. Configure Azure authentication for GitHub Actions.
3. Add required Azure and ACR values as GitHub repository secrets.
4. Create a GitHub Actions workflow.
5. Build the container artifact from the repository.
6. Tag the image with a version or commit SHA.
7. Push the image to Azure Container Registry.
8. Validate that the artifact exists in ACR.
9. Use the artifact later for AKS, App Service, or another Azure deployment target.

## Validation

After the workflow runs successfully, validate the image in Azure Container Registry:

```bash
az acr repository list --name <acr-name> --output table
```

To view tags for a specific repository:

```bash
az acr repository show-tags \
  --name <acr-name> \
  --repository <repository-name> \
  --output table
```

## Portfolio Positioning

This project is part of my cloud engineering portfolio and highlights skills in:

- Azure cloud engineering
- CI/CD pipeline automation
- Secure artifact management
- GitHub Actions
- Azure Container Registry
- DevOps practices
- Platform engineering foundations

## LinkedIn Featured Summary

Built a secure CI/CD artifact pipeline using GitHub Actions and Azure Container Registry. This project demonstrates cloud engineering, DevOps automation, secure container artifact management, and platform engineering fundamentals.
