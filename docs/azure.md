Q1. Your company wants to migrate applications from On-Premises to Azure. What approach would you follow?

Answer:
I would start with an assessment of the existing infrastructure using Azure Migrate to understand dependencies, resource utilization, and migration readiness.
Next, I would build an Azure Landing Zone to establish governance, security, networking, and monitoring standards. For connectivity, I would use VPN Gateway or ExpressRoute depending on business requirements.
For server migration, I would use Azure Site Recovery (ASR), and for database migration, I would use Azure Database Migration Service (DMS). After migration, I would continuously monitor the environment using Azure Monitor and Log Analytics Workspace to ensure application performance and stability.

Q2. Your application is not accessible from the internet. How would you troubleshoot the issue?

Answer:
I would follow a layered troubleshooting approach.
First, I would verify whether traffic is reaching the Azure environment using Azure Network Watcher and Connection Troubleshoot. Then I would review NSG rules, Azure Firewall policies, Route Tables, and Application Gateway or Load Balancer configurations.
I would also check the backend health status of the Application Gateway and analyze logs through Azure Monitor and Log Analytics Workspace. This helps identify exactly where the traffic is getting blocked.

Q3. A company wants secure access to Azure VMs without exposing them to the internet. What solution would you recommend?

Answer:
I would recommend Azure Bastion.
Azure Bastion allows administrators to access Azure Virtual Machines through RDP or SSH directly from the Azure Portal without assigning public IP addresses.
To strengthen security further, I would integrate it with Microsoft Entra ID (Azure AD), implement RBAC, and configure Just-In-Time (JIT) Access using Microsoft Defender for Cloud.

Q4. Your organization has multiple Azure subscriptions. How would you manage governance and compliance?

Answer:
I would use Management Groups to organize subscriptions and apply governance centrally.
To enforce compliance, I would implement Azure Policies that restrict resource creation based on organizational standards. Access would be managed using RBAC, and costs would be monitored through Azure Cost Management.
I would also implement resource tagging standards and use Azure Monitor for centralized monitoring and compliance reporting.

Q5. A business-critical web application needs protection against SQL Injection and Cross-Site Scripting attacks. What Azure service would you use?

Answer:
I would use Azure Application Gateway with Web Application Firewall (WAF).
Application Gateway provides Layer-7 load balancing, URL-based routing, and SSL termination, while WAF protects against common web attacks such as SQL Injection, Cross-Site Scripting (XSS), and other OWASP Top 10 vulnerabilities.
For monitoring security events and attack patterns, I would use Azure Monitor, Log Analytics Workspace, and Microsoft Defender for Cloud.

Q6. Your company requires connectivity between On-Premises and Azure. Which solution would you choose?

Answer:
The choice depends on business requirements.
For secure communication over the public internet, I would use VPN Gateway. For enterprise workloads requiring dedicated, private, and high-bandwidth connectivity, I would recommend ExpressRoute.
To monitor connectivity and troubleshoot network issues, I would use Network Watcher and secure the environment with Azure Firewall.

Q7. A production application is experiencing performance issues. How would you investigate?

Answer:
I would start by reviewing infrastructure and application metrics using Azure Monitor and Application Insights.
I would analyze CPU utilization, memory consumption, disk I/O, network latency, dependency failures, and application response times. Logs would be reviewed through Log Analytics Workspace.
Additionally, I would use Azure Advisor to identify optimization recommendations and determine whether the issue is infrastructure-related or application-related.

Q8. Your company wants to securely store passwords, certificates, and connection strings. What Azure service would you use?

Answer:
I would use Azure Key Vault.
Key Vault provides centralized and secure storage for secrets, certificates, and encryption keys. Applications can securely retrieve secrets using Managed Identity, eliminating the need to hardcode credentials.
For CI/CD integration, Azure DevOps pipelines can access Key Vault secrets through service connections, ensuring secure deployments.

Q9. A developer accidentally deleted a critical Azure resource. How would you reduce the risk of such incidents?

Answer:
I would implement Resource Locks to prevent accidental deletion of critical resources.
Additionally, I would enforce RBAC with the principle of least privilege and use Azure Policy to restrict unauthorized actions.
To ensure recoverability, I would configure Azure Backup, Recovery Services Vault, and regularly review Azure Activity Logs for auditing purposes.

Q10. How would you design a highly available application in Azure?

Answer:
I would deploy workloads across multiple Availability Zones to eliminate single points of failure.
Traffic would be distributed using Azure Load Balancer or Application Gateway, and databases would use Azure SQL Geo-Replication for redundancy.
For global traffic management, I would use Azure Traffic Manager, while monitoring and alerting would be handled through Azure Monitor and Application Insights.

