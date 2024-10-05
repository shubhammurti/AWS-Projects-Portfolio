# OPS01-AWS300 - Deploy a VPC with Terraform


## Cloud Service Provider
✍️ [You need to choose a single cloud provider, unless your project is multi-cloud]

- Amazon Web Services


## Difficulty

- Level 300 (Advanced)

## Estimated Time
- One hour 

## Project's Author(s)


- [Markus Mabson ](https://www.linkedin.com/in/markus-mabson-86917a133/)

## Objectives

### You need to complete the following:
- Download terraform binaries [Terraform binaries](https://www.terraform.io/downloads.html)
- Initialize terraform working directory 
- Document your environment (Draw.io)
- Create the following with Terraform deployment
    - Virtual Private Cloud (VPC)
    - Route Tables (public/private)
    - Route Table Associations
    - Internet Gateway
    - Elastic IP
    - Nat Gateway 
    - 1 EC2 Instance in public/ Private Subnet  (Amazon  Linux 2 AMI)
    - Security Groups
- Verify connectivity of public instance / private instance 
- Delete the Terraform deployment
- Verify resources are deleted

## Architectural Diagram
![image](https://github.com/shubhammurti/AWS-Projects-Portfolio/blob/d08dd1854f5c27dbd5a10e67eb6ae4a82d070ad0/LEVEL%20300/2.%20Deploy%20a%20VPC%20with%20Terraform/Image.png)

### You need to answer the following:

## What is Infrastructure as Code (IaC)?

Infrastructure as Code (IaC) is a modern approach to managing and provisioning IT infrastructure using code and automation tools rather than manual processes. It allows for the management of servers, storage, networks, and other infrastructure components through machine-readable definition files. This approach enables:
- **Consistency:** Ensures the same infrastructure setup every time it's deployed.
- **Version Control:** Infrastructure configurations can be tracked and versioned using version control systems like Git.
- **Reproducibility:** Infrastructure can be recreated from scratch with the same configuration, reducing the risk of configuration drift.
- **Automation:** Reduces manual errors and speeds up deployment processes through automated provisioning.

## What is Terraform?

Terraform is an open-source Infrastructure as Code (IaC) tool developed by HashiCorp. It allows you to define and provision infrastructure using a high-level configuration language known as HashiCorp Configuration Language (HCL). Key features of Terraform include:
- **Declarative Configuration:** You describe the desired state of your infrastructure, and Terraform handles the provisioning and management.
- **Provider Support:** Terraform supports a wide range of cloud providers (e.g., AWS, Azure, Google Cloud) and services.
- **Resource Management:** Manages the lifecycle of infrastructure resources, including creation, updates, and deletions.
- **State Management:** Keeps track of the state of your infrastructure, ensuring changes are applied correctly.

## What is a State File Used For?

In Terraform, the state file is a critical component that stores the current state of your infrastructure. It acts as a source of truth for Terraform, mapping real-world resources to your configuration. The state file is used for:
- **Tracking Resources:** Keeps track of resources that Terraform manages, including their attributes and relationships.
- **Planning Changes:** Helps Terraform determine what changes need to be made to align the real-world infrastructure with your configuration.
- **Managing Dependencies:** Maintains information about dependencies between resources to apply changes in the correct order.
- **Storing Metadata:** Stores metadata required for operations such as resource updates and deletions.

## In What Cases Would You Use Infrastructure as Code?

Infrastructure as Code is beneficial in various scenarios, including:
- **Cloud Deployments:** Managing cloud resources such as virtual machines, databases, and networking components.
- **Multi-Environment Management:** Maintaining consistent infrastructure across multiple environments (e.g., development, staging, production).
- **Scaling Operations:** Automating the scaling of infrastructure based on load or usage requirements.
- **Disaster Recovery:** Quickly redeploying infrastructure in case of failures or disasters using version-controlled configurations.
- **Compliance and Security:** Ensuring that infrastructure adheres to security and compliance requirements through codified policies and configurations.


## References
- [Terraform](https://www.terraform.io/)
- [Terraform module registry](https://registry.terraform.io/)

## Costs
- Included in the Free Tier


## Estimated time to complete
- 60 minutes
- 2 hours

## Tips
- Indent your code to make it concise and readable
Some resources may need to wait for another resource to be created. 
- It may be useful to create a key_pair in the management UI before creating the EC2 instances

## Output
![image](https://github.com/shubhammurti/AWS-Projects-Portfolio/blob/d08dd1854f5c27dbd5a10e67eb6ae4a82d070ad0/LEVEL%20300/2.%20Deploy%20a%20VPC%20with%20Terraform/Gif.gif)
