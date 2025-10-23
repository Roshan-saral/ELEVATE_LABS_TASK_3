# 🌐 ELEVATE_LABS_TASK_3 : Create and Configure a Virtual Private Cloud (VPC) with Subnets

![AWS Badge](https://img.shields.io/badge/AWS-VPC-blue?logo=amazon-aws)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Author](https://img.shields.io/badge/Author-Roshan%20Saral%20Kumar-lightgrey)

---
## 📌 Task Objective
To learn how cloud networking works by creating a Virtual Private Cloud (VPC) with public and private subnets, and enabling controlled internet access.
This task teaches the backbone of secure cloud architecture and how resources are isolated and protected in the cloud.
---
## 🛠️ Recommended Free Tools
- ✅ **AWS Free Tier (Preferred)**  
- Services used: VPC, Subnets, Route Tables, Internet Gateway, Security Groups
  ---

## ⚙️ Configuration Steps (AWS Console)

- ✅ **Create VPC**
  - CIDR block: `10.0.0.0/16`
  - Name: `roshans_elevatelabs_vpc`

- ✅ **Create Subnets**
  - Public Subnet: `rosb_sub1_elevatelabs_public` → `10.0.1.0/24` in `ap-south-1a`
  - Private Subnet: `rosb_sub2_elevatelabs_private` → `10.0.2.0/24` in `ap-south-1b`

- ✅ **Create and Attach Internet Gateway**
  - Name: `ROSH_SUBNETS_IGW_ELEVATELABS`
  - Attach to VPC

- ✅ **Create Route Tables**
  - **Public Route Table**: `RT-01-ELEVATE-LABS-PUBLIC`
    - Route: `0.0.0.0/0 → IGW`
    - Associated with public subnet
  - **Private Route Table**: `RT-02-ELEVATE-LABS-PRIVATE`
    - No internet route
    - Associated with private subnet

- ✅ **Enable Auto-Assign Public IP**
  - Enabled for public subnet
  - Disabled for private subnet

---

## 🔐 Subnet Usage Summary

| **Subnet Name** | **Route Table** | **Internet Access** | **Purpose** |
|------------------|------------------|----------------------|-------------|
| `rosb_sub1_elevatelabs_public` | RT-01-ELEVATE-LABS-PUBLIC | ✅ Yes (via IGW) | Web server, bastion host |
| `rosb_sub2_elevatelabs_private` | RT-02-ELEVATE-LABS-PRIVATE | ❌ No | Database, internal services |

---

## 🖼️ Reference Architecture

![Network Architecture](https://vpsie.com/wp-content/uploads/2023/01/Networkinternet-getwar.gif)

This diagram illustrates a typical cloud network setup:
- Public subnets route traffic through an Internet Gateway
- Private subnets remain isolated for secure backend operations
- Route tables and security groups control traffic flow

My configuration reflects this model using custom-named AWS resources and subnet segmentation.

---

## 🖼️ VPC Workflow Visualization

![VPC Workflow](https://miro.medium.com/v2/resize:fit:1358/1*iPYRdopwH0I8odXytU2AUw.gif)

This animated diagram shows the **end-to-end flow of traffic in an AWS VPC**:
- 🌐 **Internet Gateway (IGW)** connects the public subnet to the internet
- 🧱 **Public subnet** hosts EC2 instances with public IPs, allowing inbound/outbound traffic
- 🔒 **Private subnet** hosts backend services like databases, isolated from direct internet access
- 🔁 **NAT Gateway** (optional) allows private instances to access the internet for updates without exposing them
- 🔐 **Security groups and route tables** enforce traffic rules and subnet boundaries

This workflow mirrors the architecture I implemented in `roshans_elevatelabs_vpc`, ensuring secure segmentation and scalable design.

---

## 📜 Declaration of Originality

I, **Roshan Saral Kumar**, hereby declare that the work presented in this repository is my own and has been completed without unauthorized assistance. All configurations, diagrams, and documentation reflect my personal understanding and implementation of AWS services including VPC, subnets, route tables, security groups and internet gateway setup.

This submission is intended solely for educational and professional development purposes.

Signed,  
Roshan Saral Kumar  
Date: October 23, 2025

---

## 📝 Notes

- ✅ Follows AWS best practices for subnet isolation and traffic control
- 📁 Screenshots and architecture diagrams are included in the `/files` folder
- 🔐 EC2 instance setup and application deployment (private subnet) are documented in `/files/deployment_notes.md`

---
## 🖼️ Terraform Infrastructure Animation
![Terraform Infrastructure Flow](https://camo.githubusercontent.com/e5de88896970cab0e53da7a8170a8ff59eaedf21c909fdf4592cbd72869d321f/68747470733a2f2f63646e2e686173686e6f64652e636f6d2f7265732f686173686e6f64652f696d6167652f75706c6f61642f76313635343533333937333934312f6566436b6547782d322e6769663f773d35303026683d323632266669743d63726f702663726f703d656e74726f7079266175746f3d666f726d61742c636f6d7072657373266769662d713d363026666f726d61743d7765626d)
This animated diagram illustrates how Terraform provisions cloud infrastructure step-by-step:
- 📦 Reads `.tf` files to define resources like VPCs, subnets, EC2 instances, and gateways
- ⚙️ Builds a dependency graph to determine the correct order of resource creation
- 🚀 Executes `terraform apply` to interact with the AWS API and provision infrastructure
- 🧾 Updates the state file to track all managed resources
- 🔁 Ensures repeatable, version-controlled deployments using Infrastructure as Code (IaC)
This visual reinforces how Terraform simplifies and automates the setup of secure cloud environments like `roshans_elevatelabs_vpc`.
---
## i also know terraform and it is much easier to create in terraform within a few seconds it is a iaac tool that is infrastructure as code and enables us to create platforms within seconds these are some codes and commands of terraform.
| **Scenario**                          | **Command**                                      | **Purpose**                                                                 |
|--------------------------------------|--------------------------------------------------|------------------------------------------------------------------------------|
| 🔧 Initialize project                | `terraform init`                                 | Sets up the working directory and downloads required providers               |
| 🧹 Format code                       | `terraform fmt`                                  | Auto-formats `.tf` files for readability and consistency                     |
| ✅ Validate syntax                   | `terraform validate`                             | Checks for syntax errors and misconfigurations                               |
| 📋 Preview changes                   | `terraform plan`                                 | Shows what Terraform will do before applying changes                         |
| 🚀 Apply changes                     | `terraform apply`                                | Provisions infrastructure as defined in `.tf` files                          |
| 💣 Destroy resources                 | `terraform destroy`                              | Tears down all managed resources                                             |
| 📦 Show current state                | `terraform show`                                 | Displays the current state of infrastructure                                 |
| 📂 List tracked resources            | `terraform state list`                           | Lists all resources tracked in the state file                                |
| 🔍 Inspect a resource                | `terraform state show <resource>`                | Shows details of a specific resource                                         |
| 🧪 Create new workspace              | `terraform workspace new <env>`                  | Creates a new workspace (e.g., dev, staging, prod)                           |
| 🔄 Switch workspace                 | `terraform workspace select <env>`              | Switches to a different workspace                                            |
| 📁 List workspaces                   | `terraform workspace list`                       | Lists all available workspaces                                               |
| 🔐 View output values                | `terraform output`                               | Displays output variables after apply                                        |
| 🔑 Pass variable via CLI            | `terraform apply -var="key=value"`               | Injects variables directly from command line                                 |
| 📄 Use variable file                 | `terraform apply -var-file="vars.tfvars"`        | Loads variables from a `.tfvars` file                                        |
| 🔗 Download modules                 | `terraform get`                                  | Downloads modules referenced in configuration                                |
| 📦 List providers                    | `terraform providers`                            | Lists all providers used in the configuration                                |
| 🧾 Generate dependency graph         | `terraform graph`                                | Outputs a DOT-format graph of resource dependencies                          |
| 🧪 Test with dry run                 | `terraform plan -out=tfplan`                     | Saves the plan for later execution                                           |
| 🚀 Apply saved plan                 | `terraform apply tfplan`                         | Applies the previously saved execution plan                                  |
| 🧼 Clean up local state              | `rm -rf .terraform/ terraform.tfstate*`          | Removes local state and cache (use with caution)                             |
| 🔒 Remote state with S3             | `terraform backend "s3"`                         | Configures remote state storage in S3 with optional locking via DynamoDB     |
| 📊 Audit changes                    | `terraform plan -detailed-exitcode`              | Returns exit codes to detect changes programmatically                        |
---
| **Issue** | **Command** | **Purpose / Solution** |
|-----------|-------------|-------------------------|
| 🔄 Backend not initializing | `terraform init -backend=true` | Reinitializes backend configuration for remote state |
| ❌ Provider version mismatch | `terraform providers lock` | Locks compatible provider versions to avoid upgrade conflicts |
| 🧪 Unexpected changes in plan | `terraform plan -detailed-exitcode` | Returns exit codes to detect changes programmatically |
| 🧼 Corrupted local state | `rm -rf .terraform/ terraform.tfstate*` | Removes cached state and reinitializes (use with caution) |
| 🔍 Resource not found in state | `terraform state list` | Lists all tracked resources to confirm existence |
| 🔎 Inspect resource details | `terraform state show <resource>` | Shows full attributes of a specific resource |
| 🧩 Module not loading | `terraform get -update` | Refreshes and downloads missing modules |
| 🔐 Secrets not loading | `terraform apply -var-file="secrets.tfvars"` | Loads sensitive variables from a secure file |
| 🧪 Plan shows no changes but infra is broken | `terraform refresh` | Syncs state file with actual infrastructure |
| 🔄 Resource not updating | `terraform taint <resource>` | Forces recreation of a specific resource |
| 💣 Destroy fails due to dependencies | `terraform destroy -target=<resource>` | Destroys specific resources safely |
| 🧭 Wrong workspace selected | `terraform workspace list` / `terraform workspace select <env>` | Lists and switches to correct workspace |
| 🧾 Output missing | `terraform output` | Displays output values after apply |
| 🔗 Remote state not locking | Check S3 + DynamoDB backend config | Ensure locking is enabled in backend block |
| 🧪 Plan fails with unknown error | `TF_LOG=DEBUG terraform plan` | Enables verbose logging for deeper debugging |
| 🧼 CLI cache issues | `terraform providers mirror ./cache` | Mirrors provider plugins locally to avoid download errors |
| 🧱 Resource stuck in provisioning | Check AWS Console + `terraform state show` | Compare actual AWS status with Terraform state |
---
## 🖼️ Terraform Execution Flow

![Terraform Execution Flow](https://miro.medium.com/v2/resize:fit:1358/1*rojRn0kPfvk0fKnQElqbRQ.gif)

This animated diagram shows how **Terraform automates infrastructure provisioning in AWS**:

- 📦 Terraform reads `.tf` files that define resources like VPCs, subnets, route tables, and gateways.
- ⚙️ It builds a dependency graph to understand the order of resource creation.
- 🚀 When `terraform apply` is executed, Terraform interacts with the AWS API to provision each resource in sequence.
- 🧾 A state file (`terraform.tfstate`) is updated to track all managed resources.
- 🔁 If changes are made, `terraform plan` shows the delta and `terraform apply` reconciles the infrastructure.
- 🔐 This process ensures repeatable, version-controlled infrastructure deployments using Infrastructure as Code (IaC).

This flow reflects how I could recreate the entire `roshans_elevatelabs_vpc` architecture using Terraform — securely, consistently, and within seconds.
---
## ⚠️ Challenges Faced

During the creation and configuration of the VPC architecture, I encountered several real-world challenges that helped deepen my understanding of AWS networking:

- 🔐 **Subnet Isolation Confusion**  
  Initially, I misconfigured the route tables, which accidentally exposed the private subnet to the internet. I resolved this by removing the default route and verifying subnet associations.

- 🌐 **Internet Gateway Attachment Errors**  
  The IGW wasn’t properly attached to the VPC, causing connectivity issues in the public subnet. I reattached the IGW and confirmed routing via the public route table.

- 📶 **Public IP Not Assigned Automatically**  
  EC2 instances in the public subnet didn’t receive public IPs. I learned to enable “Auto-assign public IPv4 address” in subnet settings.

- 🧭 **Route Table Misalignment**  
  I mistakenly associated the private subnet with the public route table. After troubleshooting, I created a dedicated private route table with no internet route.

- 🧱 **Terraform State Drift**  
  While testing with Terraform, I noticed discrepancies between the actual AWS console and the `.tfstate` file. I used `terraform refresh` and `terraform state show` to reconcile the differences.

- 🧪 **Naming Inconsistencies**  
  Resource names across AWS Console and Terraform files were mismatched, leading to confusion. I standardized naming conventions for clarity and traceability.

These challenges strengthened my troubleshooting skills and taught me how to build secure, production-ready cloud infrastructure using both the AWS Console and Terraform.
---
## ✅ Conclusion

This VPC setup lays the foundation for a secure and scalable cloud architecture in AWS. By implementing:

- 🔹 A custom VPC (`roshans_elevatelabs_vpc`) with a well-defined CIDR block
- 🔹 Segregated public and private subnets across multiple availability zones
- 🔹 Dedicated route tables for controlled traffic flow
- 🔹 An Internet Gateway for public access and subnet-level isolation

I’ve followed AWS best practices to ensure clarity, modularity, and security. This architecture is ready to support real-world workloads such as web servers, bastion hosts, and backend databases — with room to expand into NAT gateways, VPNs, and hybrid cloud setups.

This project reflects my ability to design infrastructure that is production-ready, auditable, and aligned with corporate standards for cloud networking.






