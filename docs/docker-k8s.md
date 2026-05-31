Docker
Q1. Your application works on your laptop but fails in production. How would Docker help?
Answer

Docker packages the application along with all its dependencies, libraries, and runtime configurations into a container image.

This ensures that the application behaves consistently across Development, QA, and Production environments, eliminating the "Works on My Machine" problem.

Tools Used
Docker
Dockerfile
Docker Hub
Azure Container Registry (ACR)
Q2. A container keeps restarting repeatedly. How would you troubleshoot it?
Answer

I would first check the container logs to identify application startup errors.

Then I would verify environment variables, configuration files, network connectivity, resource limits, and application dependencies. Most restart issues occur because the application inside the container fails to start properly.

Tools Used
Docker Logs
Docker Inspect
Docker Stats
Azure Monitor
Q3. Your container image size is 2GB. How would you optimize it?
Answer

I would use a lightweight base image such as Alpine Linux and implement multi-stage builds.

I would also remove unnecessary packages, clean temporary files, and include only required application dependencies in the final image.

This reduces image size, improves security, and speeds up deployments.

Tools Used
Dockerfile
Multi-Stage Build
Alpine Linux
Docker Scout
Q4. How do you securely store secrets in Docker?
Answer

Secrets should never be hardcoded inside Docker images.

I would store them in Azure Key Vault or Kubernetes Secrets and inject them into containers during runtime. This improves security and simplifies secret rotation.

Tools Used
Azure Key Vault
Docker Secrets
Kubernetes Secrets
Managed Identity
Q5. How do you scan Docker images for vulnerabilities?
Answer

Before deployment, I would scan container images for known vulnerabilities.

If critical vulnerabilities are found, the pipeline should fail automatically and deployment should be blocked until the issues are resolved.

Tools Used
Trivy
Docker Scout
Microsoft Defender for Containers
GitHub Security Scanning
Kubernetes
Q6. Your Pod is showing CrashLoopBackOff. How would you troubleshoot it?
Answer

I would first inspect the Pod logs and Kubernetes events.

Then I would verify application startup commands, environment variables, image versions, ConfigMaps, Secrets, and resource limits. CrashLoopBackOff usually indicates that the application inside the container is failing repeatedly.

Tools Used
kubectl logs
kubectl describe pod
Azure Monitor Container Insights
Lens IDE
Q7. Your application traffic suddenly increased. How would you handle it?
Answer

I would implement Horizontal Pod Autoscaler (HPA) to automatically increase the number of Pods based on CPU or memory utilization.

Additionally, I would configure Cluster Autoscaler to add more worker nodes if required.

Tools Used
HPA
Cluster Autoscaler
AKS
Azure Monitor
Q8. A Pod cannot communicate with another service. How would you troubleshoot?
Answer

I would verify Service configuration, DNS resolution, Network Policies, Ingress rules, and application ports.

I would also check whether the target Pod is healthy and receiving traffic correctly.

Tools Used
kubectl
CoreDNS
Network Policies
Azure Network Watcher
Q9. How would you expose an application running in Kubernetes to internet users?
Answer

For enterprise applications, I would use an Ingress Controller instead of exposing multiple Load Balancers.

Ingress provides centralized routing, SSL termination, path-based routing, and better traffic management.

Tools Used
NGINX Ingress Controller
Azure Application Gateway Ingress Controller (AGIC)
Azure Load Balancer
Cert Manager
Q10. Your deployment succeeded, but users are getting errors. What would you check?
Answer

I would verify Pod health, application logs, readiness probes, liveness probes, service configuration, and ingress routing.

Even if deployment succeeds, the application may fail due to configuration or dependency issues.

Tools Used
kubectl logs
kubectl describe
Azure Monitor
Application Insights
Q11. How do you perform zero-downtime deployments in Kubernetes?
Answer

I would use Rolling Updates so that new Pods are created gradually while old Pods are terminated one by one.

This ensures users continue to access the application without interruption.

Tools Used
Kubernetes Deployment
Rolling Update Strategy
AKS
Helm
Q12. How would you manage application configuration in Kubernetes?
Answer

I would store non-sensitive configuration in ConfigMaps and sensitive information in Secrets.

This allows configuration changes without rebuilding container images.

Tools Used
ConfigMaps
Kubernetes Secrets
Azure Key Vault CSI Driver
Q13. How do you monitor Kubernetes workloads?
Answer

I would monitor cluster health, node utilization, Pod status, application metrics, and logs.

Proactive monitoring helps identify performance issues before they impact users.

Tools Used
Azure Monitor Container Insights
Prometheus
Grafana
Log Analytics Workspace
Q14. A node becomes unhealthy in AKS. What happens?
Answer

Kubernetes automatically detects the unhealthy node and reschedules Pods to healthy nodes.

If Cluster Autoscaler is enabled, AKS can provision additional nodes to maintain application availability.

Tools Used
AKS
Cluster Autoscaler
Azure Monitor
Kubernetes Scheduler
Q15. How would you design a production-ready AKS architecture?
Answer

I would deploy AKS across multiple Availability Zones with separate node pools for system and application workloads.

Ingress would be managed using Application Gateway, secrets stored in Azure Key Vault, monitoring enabled through Azure Monitor, and container images stored in Azure Container Registry.

This architecture provides security, scalability, high availability, and operational efficiency.

Tools Used
AKS
Azure Container Registry (ACR)
Azure Key Vault
Application Gateway
Azure Monitor
HPA
Cluster Autoscaler
Availability Zones
Q16. Your application requires persistent storage. How would you implement it in Kubernetes?
Answer

Containers are ephemeral, so data stored inside a container can be lost if the container is restarted or deleted.

To provide persistent storage, I would use Persistent Volumes (PV) and Persistent Volume Claims (PVC). In AKS, I would integrate Azure Managed Disks or Azure Files to store application data persistently.

Tools Used
Persistent Volume (PV)
Persistent Volume Claim (PVC)
Azure Managed Disk
Azure Files
AKS
Q17. One Pod is consuming excessive CPU and affecting other workloads. How would you handle it?
Answer

I would define resource requests and limits for the Pod.

Resource requests ensure the Pod gets minimum required resources, while limits prevent it from consuming excessive CPU or memory.

This helps maintain cluster stability and prevents resource starvation.

Tools Used
Resource Requests
Resource Limits
kubectl top
Azure Monitor
Q18. How would you perform application upgrades without downtime?
Answer

I would use Rolling Updates in Kubernetes.

During deployment, Kubernetes gradually replaces old Pods with new ones while keeping the application available. Readiness and Liveness Probes ensure traffic is routed only to healthy Pods.

Tools Used
Kubernetes Deployment
Rolling Updates
Readiness Probe
Liveness Probe
Helm
Q19. How would you deploy the same application to Dev, QA, and Production environments?
Answer

I would use separate namespaces and environment-specific configuration files.

Helm charts can be reused across environments while maintaining different values files for Dev, QA, and Production.

Tools Used
Kubernetes Namespace
Helm
ConfigMaps
Azure DevOps
GitHub Actions
Q20. A Kubernetes cluster has hundreds of microservices. How would you manage deployments efficiently?
Answer

I would use Helm charts to standardize deployments and GitOps practices for configuration management.

This allows teams to deploy, upgrade, and rollback applications consistently across environments.

Tools Used
Helm
ArgoCD
GitOps
AKS
GitHub
Q21. How would you secure communication between microservices in Kubernetes?
Answer

I would implement Network Policies to control Pod-to-Pod communication and use a Service Mesh for encrypted communication.

This ensures only authorized services can communicate with each other.

Tools Used
Network Policies
Istio
Linkerd
AKS
Q22. How would you implement disaster recovery for Kubernetes workloads?
Answer

I would back up Kubernetes manifests, persistent volumes, and application configurations.

For AKS, I would use backup solutions and maintain infrastructure as code using Terraform to quickly recreate environments if needed.

Tools Used
Velero
Azure Backup
AKS Backup
Terraform
GitHub
Q23. Your cluster has become slow and unstable. How would you troubleshoot?
Answer

I would check node utilization, Pod resource consumption, pending Pods, and cluster events.

I would also review monitoring dashboards and logs to identify bottlenecks affecting cluster performance.

Tools Used
kubectl top nodes
kubectl top pods
Azure Monitor
Prometheus
Grafana
Q24. How would you implement centralized logging in Kubernetes?
Answer

Instead of checking logs on individual Pods, I would forward logs to a centralized logging platform.

This enables faster troubleshooting, searching, and monitoring across all applications.

Tools Used
Azure Monitor
Log Analytics Workspace
Fluent Bit
Elasticsearch
Kibana

Q25. Your organization wants a production-ready Kubernetes platform. What best practices would you implement?
Answer

I would implement namespace isolation, RBAC, network policies, autoscaling, monitoring, centralized logging, backup strategies, and Infrastructure as Code.

I would also secure secrets using Azure Key Vault and automate deployments through CI/CD pipelines.

Tools Used
AKS
Azure Key Vault
Azure Monitor
Prometheus
Grafana
ArgoCD
Terraform
Azure DevOps
GitHub Actions