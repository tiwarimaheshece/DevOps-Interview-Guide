Terraform Scenario-Based Interview Questions & Answers

Q1. Your team consists of multiple engineers working on the same Terraform codebase. How would you prevent state file conflicts?
Answer

In a team environment, storing the Terraform state file locally is not recommended because multiple engineers may overwrite each other's changes.

I would use a remote backend such as Azure Storage Account to store the state file centrally. Additionally, I would enable state locking so that only one person can modify the infrastructure at a time.

This prevents state corruption and ensures infrastructure consistency across the team.

Q2. A production VM was manually deleted from Azure. What will happen when you run Terraform Apply?
Answer

Terraform compares the actual infrastructure with the state file and configuration.

Since the VM exists in the Terraform state but not in Azure, Terraform will detect the drift and attempt to recreate the VM during the next Terraform Apply.

This is one of the major advantages of Infrastructure as Code because it helps maintain the desired state automatically.

Q3. Your Terraform deployment is failing because a resource already exists in Azure. How would you handle it?
Answer

This usually happens when the resource was created manually outside Terraform.

Instead of recreating the resource, I would use the Terraform Import command to bring the existing resource into the Terraform state file.

After importing, I would update the Terraform configuration to match the existing resource and then run Terraform Plan to verify the changes.

Q4. How would you manage Dev, QA, and Production environments using the same Terraform code?
Answer

I would create reusable Terraform modules and maintain separate variable files for each environment.

For example:

dev.tfvars
qa.tfvars
prod.tfvars

This approach allows us to maintain a single codebase while deploying environment-specific configurations such as VM sizes, instance counts, and networking settings.

Q5. During a deployment, Terraform shows that it wants to delete a production database. What would you do?
Answer

I would never directly execute Terraform Apply in this situation.

First, I would carefully review the Terraform Plan output to understand why Terraform is proposing the deletion.

For critical resources such as databases, I would use:

lifecycle {
  prevent_destroy = true
}

I would also verify recent code changes and obtain proper approvals before making any modifications.

Q6. How would you securely store Terraform state files in Azure?
Answer

I would use an Azure Storage Account with a Blob Container as the remote backend.

To improve security, I would:

Enable private endpoints
Restrict public access
Enable encryption at rest
Enable blob versioning
Use RBAC for access control

This ensures that the state file remains secure and recoverable.

Q7. Your Terraform deployment is successful, but the application team reports that the infrastructure is not working correctly. How would you troubleshoot?
Answer

I would follow a structured troubleshooting approach.

First, I would verify the Terraform Apply logs to confirm that all resources were created successfully.

Then I would validate:

Network connectivity
NSG rules
Load Balancer configuration
DNS resolution
Application health

Sometimes Terraform successfully creates resources, but application-level configuration issues still exist.

Q8. How would you implement Terraform in a CI/CD pipeline?
Answer

In my projects, Terraform deployments are automated through Azure DevOps or GitHub Actions pipelines.

A typical flow is:

Code Commit
Terraform Init
Terraform Validate
Terraform Plan
Security Scanning (TFSec, Checkov, TFLint)
Approval Stage
Terraform Apply

This approach ensures infrastructure changes are reviewed, tested, and securely deployed.

Q9. What would you do if the Terraform state file gets corrupted?
Answer

If the state file becomes corrupted, I would first stop all Terraform operations to avoid further damage.

If a remote backend is being used, I would restore the latest healthy version of the state file from storage versioning or backup.

After restoration, I would run Terraform Plan to verify that the state and infrastructure are synchronized.

Q10. Your company wants to deploy the same infrastructure across multiple Azure subscriptions. How would you design it?
Answer

I would create reusable Terraform modules and use provider aliases to manage multiple subscriptions.

Each subscription would have its own backend configuration and environment variables.

This design allows centralized code management while maintaining isolation between Development, QA, and Production subscriptions.