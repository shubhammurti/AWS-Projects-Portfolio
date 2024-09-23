# OPS01-AWS100 — Deploy a CloudFormation template from the AWS Console

## Cloud Service Provider

- Amazon Web Services

## Difficulty

- Level 100 (Introductory)

## Estimated Time
- One hour

## Project's Author(s)
- [Syed Auther](https://twitter.com/syedauther)
- [Chris Nagy](https://twitter.com/chris_the_nagy)

## Objectives

### You need to complete the following:

- Download our simple, pre-made [CloudFormation template](./OPS01-AWS100-CFTEMPLATE.yaml?raw=true)
- Go to the CloudFormation Console in AWS
- Choose _create stack with new resources_ and use the template file from above
- At the _"Configure stack options"_ page, leave everything on default
- Watch as CloudFormation deploys the resources, check the _events_ tab to see what is being created
- Make sure that there is a new DynamoDB Table, and a new S3 bucket deployed
- Delete the stack in the CloudFormation console
- Make sure both resources got deleted

### You need to answer the following: 

## What is Infrastructure as Code (IaC)?

**Infrastructure as Code (IaC)** is a practice that allows you to manage and provision computing infrastructure through code, rather than through manual processes. IaC automates the deployment of resources such as servers, databases, and networks, making infrastructure scalable, repeatable, and consistent. It enables the versioning and management of infrastructure in the same way developers manage code, facilitating continuous integration and delivery (CI/CD) pipelines.

## What is CloudFormation?

**AWS CloudFormation** is a service that allows you to model, provision, and manage AWS resources using Infrastructure as Code (IaC). With CloudFormation, you can define the infrastructure and services you need using a template, and AWS CloudFormation handles the provisioning and configuration of those resources in a consistent and repeatable manner.

## What is a CloudFormation template?

A **CloudFormation template** is a JSON or YAML file that defines the desired resources and configurations within your AWS environment. The template specifies the resources (such as EC2 instances, S3 buckets, or RDS databases), their properties, and any dependencies between them. Templates provide a declarative way to describe the infrastructure and can be reused across environments and regions.

## In what two file formats can a CloudFormation template be specified?

CloudFormation templates can be written in:
- **JSON (JavaScript Object Notation)** format
- **YAML (YAML Ain't Markup Language)** format

## What is a CloudFormation stack?

A **CloudFormation stack** is a collection of AWS resources that you create and manage as a single unit using a CloudFormation template. The stack provisions, configures, and manages all the resources defined in the template. You can create, update, or delete resources in a stack as a group, simplifying the process of managing complex environments.

## Can the same template be used in other regions?

Yes, the same **CloudFormation template** can be used to create stacks in other AWS regions. Since CloudFormation templates are region-agnostic, they can be reused to deploy resources in different regions, assuming the services and resources defined in the template are available in the target region.

## What happens to the deployed resources when the stack gets deleted?

When a **CloudFormation stack** is deleted, by default, all the resources that were created as part of the stack are also deleted. CloudFormation performs a cleanup of all associated resources, such as EC2 instances, RDS databases, and S3 buckets, unless they are explicitly marked for retention in the template.

## References

- [CloudFormation Introduction](https://www.youtube.com/watch?v=GeERpAAKCsQ&list=PLBfufR7vyJJ6FhBhJJSaMkI-m2wyoPy-G&index=200)
- [AWS - Deploy a CloudFormation stack](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/GettingStarted.Walkthrough.html#GettingStarted.Walkthrough.createstack)
- [CloudFormation Template structure](https://www.youtube.com/watch?v=NhQhltDp1o4&list=PLBfufR7vyJJ6FhBhJJSaMkI-m2wyoPy-G&index=202)

## Costs
- This project is included in the free tier

## Output
![image](https://github.com/user-attachments/assets/8b843db8-dad2-4199-a7bc-87f2fbaf43b5)
