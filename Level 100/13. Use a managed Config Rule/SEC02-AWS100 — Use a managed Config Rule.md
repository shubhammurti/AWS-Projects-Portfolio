# SEC02-AWS100 — Use a managed Config Rule

## Cloud Service Provider
- Amazon Web Services

## Difficulty

- Level 100 (Introductory)

## Estimated Time

1 hour

## Project's Author(s)

- [Andrew Brown](https://twitter.com/andrewbrown)

## Objectives

### You need to complete the following:

- Turn on AWS Config in the US-EAST-1 region
- Choose the managed Config rule eg. encrypted-volumes
- Launch an EC2 instance without an encryped EBS volume
- Monitor AWS Config until it detects there is an EBS volume that is unencrpyted

### You need to answer the following:

## What is AWS Config?

**AWS Config** is a fully managed service that provides detailed historical records of AWS resource configurations, their relationships, and changes over time. It helps you assess, audit, and evaluate the configurations of your AWS resources to ensure they comply with your internal policies and industry standards. AWS Config enables you to:

- **Track Resource Changes**: Record and monitor changes to AWS resources and their configurations.
- **Compliance Auditing**: Evaluate resource configurations against compliance policies and industry standards.
- **Configuration History**: View historical configurations to understand how resources have changed over time.
- **Change Management**: Analyze changes and their impact on your AWS environment.

## What does an AWS Config rule do?

An **AWS Config rule** is a predefined or custom rule that evaluates the configuration of AWS resources against desired configurations or compliance standards. AWS Config rules help you:

- **Automate Compliance Checks**: Continuously evaluate resources against predefined compliance rules to ensure they adhere to policies.
- **Detect Non-compliance**: Identify resources that do not comply with the specified configurations or standards.
- **Trigger Actions**: Automatically respond to non-compliance by triggering remediation actions or notifications.
- **Custom Rules**: Create custom rules using AWS Lambda functions to evaluate specific resource configurations.

## What is remediation in the context of a config rule?

**Remediation** in AWS Config refers to the actions taken to correct or address non-compliance detected by a Config rule. Remediation helps ensure that resources comply with desired configurations and policies. It includes:

- **Automated Remediation**: Automatically apply predefined actions to correct non-compliant resources, such as changing resource configurations or settings.
- **Manual Remediation**: Provide recommendations or notifications for manual intervention by administrators to address compliance issues.
- **Remediation Actions**: Define specific actions or Lambda functions to be executed in response to non-compliance, such as modifying resource attributes or updating security group rules.

## References

- [AWS Config](https://aws.amazon.com/config/)
- [List of AWS Config Managed Rules](https://docs.aws.amazon.com/config/latest/developerguide/managed-rules-by-aws-config.html)

## Output 
![image](https://github.com/shubhammurti/AWS-Projects-Portfolio/blob/584208a8e10883f5fcb59de46c617eb2907846d3/Level%20100/13.%20Use%20a%20managed%20Config%20Rule/config.png)
