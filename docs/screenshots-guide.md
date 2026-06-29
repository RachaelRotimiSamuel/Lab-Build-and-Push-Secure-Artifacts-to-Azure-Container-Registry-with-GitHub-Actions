# Screenshots Guide

Screenshots make a cloud portfolio repository more credible because they show that the project was actually built and validated.

Use this guide to capture proof of completion.

## Recommended Screenshot Folder

Create this folder in the repository:

```text
assets/screenshots/
```

## Screenshot 1: GitHub Actions Workflow Run

Capture a screenshot showing:

- Workflow name
- Successful run status
- Commit that triggered the workflow
- Build and push steps completed

Suggested file name:

```text
assets/screenshots/github-actions-success.png
```

## Screenshot 2: Azure Container Registry Overview

Capture a screenshot showing:

- ACR name
- Resource group
- Region
- SKU

Suggested file name:

```text
assets/screenshots/acr-overview.png
```

## Screenshot 3: ACR Repository List

Capture a screenshot showing the pushed image repository inside ACR.

Suggested file name:

```text
assets/screenshots/acr-repositories.png
```

## Screenshot 4: ACR Image Tags

Capture a screenshot showing image tags, ideally with a commit SHA or versioned tag.

Suggested file name:

```text
assets/screenshots/acr-image-tags.png
```

## Screenshot 5: GitHub Repository Secrets

Capture only the secret names, never the values.

Suggested file name:

```text
assets/screenshots/github-secrets-names.png
```

## Screenshot Safety Reminder

Do not expose:

- Subscription IDs if you do not want them public
- Tenant IDs
- Client secrets
- Access tokens
- Registry passwords
- Private environment variables
- Sensitive application data

Blur anything sensitive before uploading screenshots.

## Why These Screenshots Matter

Recruiters and hiring managers are more likely to trust a project when they can see evidence of:

- A successful workflow run
- Real Azure resources
- Real container artifacts
- Clear validation steps
- Security awareness
