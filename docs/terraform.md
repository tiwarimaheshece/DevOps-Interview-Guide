1. Terraform State File Lost

Q: Suppose your Terraform state file is accidentally deleted. What will you do?

Ans:
The state file is very important because Terraform uses it to track infrastructure resources. If the state file is stored remotely, I will restore it from the remote backend. If a backup state file is available, I can recover from that backup. After recovery, I will run terraform plan to verify the current infrastructure state. This is one reason why I always use a remote backend in production environments.

2. Someone Created a Resource Manually

Q: A VM was created manually in Azure Portal, but now you want Terraform to manage it. What will you do?

Ans:
Terraform can only manage resources that exist in its state file. Since the VM was created outside Terraform, I will use the terraform import command to import it into the Terraform state. After importing, I will write the corresponding Terraform code. Then I will run terraform plan to make sure Terraform does not recreate or modify the VM unexpectedly.

3. Prevent Accidental Deletion

Q: How do you protect production resources from accidental deletion?

Ans:
For critical production resources, I use the lifecycle block with prevent_destroy = true. This prevents Terraform from deleting the resource even if someone runs terraform destroy or removes the resource from the code. It provides an additional safety layer for important resources such as databases and production virtual machines.

4. Managing Multiple Environments

Q: How do you manage Dev, Test, and Production environments using Terraform?

Ans:
I keep separate variable files and separate state files for each environment. For example, I use dev.tfvars, test.tfvars, and prod.tfvars. This allows me to use the same Terraform code while deploying different configurations. It also prevents changes in one environment from affecting another environment.

5. Storing Passwords Securely

Q: How do you handle passwords and secrets in Terraform?

Ans:
I never hardcode passwords or secrets in Terraform code. Instead, I store them in services like Azure Key Vault. Terraform can securely retrieve the secrets during deployment. This approach improves security and prevents sensitive information from being exposed in source code repositories.

6. Multiple Team Members Working Together

Q: Multiple engineers are working on the same Terraform project. How do you avoid conflicts?

Ans:
I use a remote backend with state locking. In Azure, the state file is usually stored in a Storage Account. State locking ensures that only one person can modify the infrastructure at a time. This prevents corruption of the state file and avoids deployment conflicts.

7. Terraform Apply Failed

Q: Terraform apply failed in the middle of deployment. What will you do?

Ans:
First, I will check the error message and deployment logs to identify the root cause. Then I will fix the issue and run terraform plan to see the current status. Terraform will compare the existing infrastructure with the state file and show pending changes. Finally, I will run terraform apply again to complete the deployment.

8. Infrastructure Drift

Q: A team member manually deleted a VM from Azure Portal. How will you identify this?

Ans:
This situation is called infrastructure drift. I will run terraform plan and Terraform will compare the actual infrastructure with the state file. It will detect that the VM is missing and show that it needs to be recreated. This helps maintain infrastructure consistency.

9. Creating Multiple Resources

Q: You need to create 20 virtual machines. How will you do it?

Ans:
Instead of writing the same code 20 times, I will use count or for_each. This allows Terraform to create multiple resources from a single resource block. It reduces code duplication and makes the configuration easier to manage and maintain.

10. Reusing Terraform Code

Q: How do you avoid writing the same Terraform code repeatedly?

Ans:
I use Terraform modules. A module is a reusable block of code that can be used multiple times across projects. For example, I can create a module for Virtual Networks, Virtual Machines, or Storage Accounts. This improves consistency and reduces maintenance effort.

11. Resource Dependency

Q: A VM should be created only after a VNet is created. How do you handle this?

Ans:
Terraform automatically manages dependencies when one resource references another resource. If explicit dependency is required, I can use depends_on. This ensures that resources are created in the correct order and prevents deployment failures.

12. Terraform in CI/CD Pipeline

Q: How do you use Terraform in Azure DevOps Pipeline?

Ans:
The pipeline usually starts with Terraform Init, followed by Validate and Plan stages. After reviewing the plan, approval is taken for production deployments. Finally, Terraform Apply is executed. This approach enables automated and controlled infrastructure deployment.

13. Terraform Provider Upgrade

Q: You need to upgrade the Azure provider version. What steps will you follow?

Ans:
First, I will update the provider version in the Terraform configuration file. Then I will run terraform init -upgrade to download the latest provider version. After that, I will run terraform plan to check for any breaking changes before applying the update.

14. Resource Name Changed

Q: You changed a resource name in Terraform code. What can happen?

Ans:
Terraform may think that the old resource should be deleted and a new resource should be created. This can cause downtime in production environments. To avoid this situation, I can use terraform state mv to update the resource name in the state file without recreating the resource.

15. Production Deployment Failed

Q: A production Terraform deployment failed. How will you troubleshoot it?

Ans:
First, I will review the pipeline logs and error messages. Then I will run terraform plan to understand the current infrastructure state. I will verify permissions, backend configuration, and resource dependencies. After fixing the issue, I will rerun the deployment. My goal is always to make minimal changes and avoid impacting production services.