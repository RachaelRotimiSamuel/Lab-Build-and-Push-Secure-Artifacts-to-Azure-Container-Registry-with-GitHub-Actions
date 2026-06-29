# Lessons Learned and Future Improvements

## Lessons Learned

### 1. Artifact pipelines are the foundation of container delivery

Before an application can be deployed into AKS or another container platform, the team needs a reliable way to build and store artifacts.

This project reinforces the importance of creating a repeatable build-and-push workflow.

### 2. Manual builds create risk

Manual builds can lead to inconsistent results because different developers may build images differently.

Automating the process through GitHub Actions creates a cleaner and more reliable delivery pattern.

### 3. ACR supports a stronger Azure deployment model

Azure Container Registry gives teams a centralized location for storing container images before deployment into Azure services.

This helps support cloud-native architecture and platform engineering workflows.

### 4. Secrets should never be hardcoded

Authentication values and registry information should be stored securely using GitHub Secrets or a stronger production-grade pattern such as OpenID Connect.

### 5. Traceable tags matter

Using a commit SHA or version tag makes it easier to connect a container image back to the exact source code that produced it.

## Future Improvements

### 1. Add OpenID Connect authentication

A future version should use GitHub Actions OIDC with Azure instead of long-lived credentials.

This would improve the security posture of the pipeline.

### 2. Add image scanning

The pipeline could include container vulnerability scanning before pushing to ACR.

Possible tools include:

- Microsoft Defender for Cloud
- Trivy
- GitHub Advanced Security
- Docker Scout

### 3. Add AKS deployment stage

The next phase could deploy the pushed image into Azure Kubernetes Service.

This would turn the project into a full build-push-deploy pipeline.

### 4. Add environment promotion

Future pipeline stages could support:

- Development
- Test
- Staging
- Production

This would better reflect enterprise release patterns.

### 5. Add approval gates

Manual approval gates could be added before production deployment.

This would show stronger release governance and change control.

### 6. Add monitoring and alerting

Future work could include monitoring the deployment with:

- Azure Monitor
- Log Analytics
- Application Insights
- GitHub Actions run alerts

## Portfolio Takeaway

This project shows a strong foundation in secure CI/CD, Azure artifact management, DevOps automation, and platform engineering thinking.
