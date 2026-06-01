Q1. Explain the CI/CD pipeline you implemented in your project.

Answer:
In my project, developers push code to GitHub. The pipeline is automatically triggered and starts with code checkout.
The first stage performs validation such as Terraform Validate, Terraform Plan, and code quality checks. The second stage runs security scans using TFSec, Checkov, and TFLint. After approval, infrastructure is deployed using Terraform and the application is deployed to AKS.
Finally, post-deployment validation and monitoring checks are performed.

Tools Used
Azure DevOps Pipelines
GitHub Actions
Terraform
TFSec
Checkov
TFLint
AKS

Q2. How do you manage secrets in CI/CD pipelines?

Answer:
I never store secrets directly in repositories or pipeline YAML files.
For Azure DevOps, I integrate Azure Key Vault with Variable Groups. For GitHub Actions, I use GitHub Secrets. Applications and pipelines retrieve secrets dynamically during execution.
This approach improves security and prevents credential exposure.
Tools Used
Azure Key Vault
Azure DevOps Variable Groups
GitHub Secrets
Managed Identity

Q3. Production deployment requires approval before release. How would you implement it?

Answer:
I would configure Environment Approvals in Azure DevOps or Environment Protection Rules in GitHub Actions.

Before the deployment stage starts, an authorized person such as a Release Manager must approve the deployment request.

This prevents unauthorized production releases.

Tools Used
Azure DevOps Environments
GitHub Environments
Approval Gates

Q4. A deployment failed in production. What would you do?

Answer:
First, I would analyze pipeline logs to identify the root cause.

If the deployment impacted users, I would immediately perform a rollback to the last stable version. After fixing the issue, I would redeploy through the pipeline and verify application health.
Tools Used
Azure DevOps
GitHub Actions
Kubernetes Rollback
Application Insights
Azure Monitor

Q5. How do you implement security scanning in your CI/CD pipeline?

Answer:
I integrate security scanning during the pipeline execution before deployment.

Infrastructure code is scanned using TFSec, Checkov, and TFLint. Container images are scanned using Trivy. If critical vulnerabilities are detected, the pipeline fails automatically.

Tools Used
TFSec
Checkov
TFLint
Trivy
SonarQube

Q6. How would you deploy an application to AKS through a pipeline?

Answer:
The pipeline first builds the Docker image and pushes it to Azure Container Registry (ACR).

After that, AKS deployment manifests or Helm charts are applied to the cluster. Finally, health checks are performed to verify the deployment.

Tools Used
Azure DevOps
GitHub Actions
Docker
AKS
ACR
Helm
kubectl

Q7. What is the difference between Microsoft-hosted and Self-hosted Agents?

Answer:
Microsoft-hosted agents are managed by Microsoft and are automatically provisioned for pipeline execution.
Self-hosted agents run on company-managed servers and provide greater control, custom tooling, and access to internal resources.
For enterprise environments, self-hosted agents are commonly used.
Tools Used
Azure DevOps Agents
GitHub Self-Hosted Runners

Q8. Your pipeline takes 40 minutes to complete. How would you optimize it?

Answer:
I would identify bottlenecks by reviewing pipeline execution logs.
Optimization techniques include parallel job execution, dependency caching, reusable templates, incremental builds, and reducing unnecessary steps.
Tools Used
Azure DevOps Pipelines
GitHub Actions Cache
Docker Layer Caching
SonarQube

Q9. How would you implement Blue-Green Deployment?

Answer:
I would maintain two identical environments: Blue and Green.
The new version is deployed to the inactive environment first. After validation, traffic is switched to the new environment with minimal downtime.
If issues occur, traffic can quickly be routed back to the previous version.
Tools Used
Azure Application Gateway
AKS
Azure Traffic Manager
Azure DevOps

Q10. How would you implement Canary Deployment?

Answer:
In Canary Deployment, a small percentage of traffic is routed to the new version initially.
The application is monitored closely, and if no issues are detected, traffic is gradually increased until the new version serves all users.
Tools Used
AKS
Istio
NGINX Ingress
Azure Monitor
Application Insights

Q11. A Terraform deployment should only run after code review. How would you enforce it?

Answer:
I would implement Pull Request validation policies.
Terraform Plan would run automatically during the PR process. The Apply stage would only execute after successful reviews and approvals.
This prevents unauthorized infrastructure changes.
Tools Used
GitHub Pull Requests
Azure Repos
Branch Policies
Terraform

Q12. How do you handle Infrastructure and Application deployments in the same pipeline?

Answer:
I separate them into stages.
The first stage provisions infrastructure using Terraform. Once successful, the application deployment stage builds and deploys the application.
This separation improves maintainability and troubleshooting.
Tools Used
Azure DevOps Multi-Stage Pipeline
GitHub Actions Workflow
Terraform
AKS

Q13. Your AKS deployment succeeded but Pods are failing. What would you check?

Answer:
I would review deployment logs, Pod logs, events, resource limits, image pull issues, and configuration settings.
I would also validate Kubernetes manifests and ingress configuration.
Tools Used
kubectl
Azure Monitor Container Insights
AKS
Helm

Q14. How do you store reusable pipeline code?

Answer:
I use YAML templates and reusable workflows.
This reduces duplication and ensures consistency across multiple projects.
Tools Used
Azure DevOps YAML Templates
GitHub Reusable Workflows

Q15. How would you design an enterprise-grade CI/CD pipeline?

Answer:
The pipeline would include:
Source Code Management
Build Stage
Unit Testing
Security Scanning
Terraform Validation
Terraform Plan
Approval Stage
Terraform Apply
Application Deployment
Monitoring & Validation
This ensures security, compliance, automation, and reliability.
Tools Used
GitHub
Azure DevOps
Terraform
SonarQube
TFSec
Checkov
Trivy
AKS
ACR
Azure Monitor
Application Insights
