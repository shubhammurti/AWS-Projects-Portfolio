# COM03-AWS200 - Create an Auto Scaling Group

## Cloud Service Provider
- Amazon Web Services

## Difficulty
- Level 200 (Intermediate)

## Project's Author(s)

[Chris Nagy](https://twitter.com/chris_the_nagy)

## Objectives

### You need to complete the following:
- Create a Launch Configuration
- Create an Auto Scaling Group with a minimum of two and maximum of five EC2 instances
- Terminate one instance manually
- After the ASG is in place, increase the desired number of instances to three
- Delete all the resources you created

### You need to answer the following:

## **What are the key differences between a Launch Template and Launch Configuration?**
*Launch Templates* support new EC2 instance features and advanced configurations like multiple instance types, mixed instances, and the ability to include Spot Instances. *Launch Configurations* are simpler but no longer support new EC2 features released after December 31, 2022. Launch Templates are more flexible and are recommended for modern Auto Scaling setups.

## **What happens if you terminate one of the running instances in an ASG manually?**
If you manually terminate a running instance in an Auto Scaling Group (ASG), the ASG will automatically launch a new instance to replace it, ensuring that the number of instances remains at the desired capacity.

## **How can you set and change the minimum, desired, and maximum number of instances in an ASG?**
You can set the minimum, desired, and maximum number of instances when creating or updating the ASG through the AWS Management Console, CLI, or API:
- **Minimum**: The least number of instances that should always be running.
- **Desired**: The ideal number of instances that the ASG tries to maintain.
- **Maximum**: The maximum number of instances the ASG can scale up to.

You can modify these values by editing the ASG in the EC2 Auto Scaling section.

## **Based on what metrics can an ASG spin up / spin down instances?**
An ASG can scale instances based on predefined metrics such as:
- **CPU Utilization**
- **Memory Utilization** (requires CloudWatch agent)
- **Request rates** (e.g., Application Load Balancer request count)
- **Custom CloudWatch metrics**
Scaling policies can trigger instance scaling up or down based on these metrics.

## **What EC2 configuration settings can you set in a Launch Template/Configuration?**
In both a Launch Template and a Launch Configuration, you can set:
- AMI ID (Amazon Machine Image)
- Instance type
- Key pair for SSH access
- Security groups
- Storage configurations (EBS volumes)
- IAM role
- User data (for instance initialization)
In a Launch Template, you can also specify advanced options like multiple instance types, Spot instances, and purchasing options.

## **Can you use Spot instances with a Launch Template/Configuration?**
Yes, you can use Spot Instances with a *Launch Template*. You cannot use Spot Instances with a *Launch Configuration*. Launch Templates allow you to specify the instance purchasing option (On-Demand or Spot).

## **How many subnets and regions can a single ASG utilize?**
A single Auto Scaling Group can span across **multiple subnets within the same region**, but it cannot span across multiple regions. Each ASG is region-specific but can distribute instances across Availability Zones within the selected region.

## **What is the difference between "desired capacity" and "minimum capacity"?**
- **Desired capacity** is the target number of instances that the ASG aims to maintain under normal conditions.
- **Minimum capacity** is the least number of instances that the ASG should never fall below, even when scaling down.

## **In which order will EC2 instances be terminated in case of a scale-in event?**
The termination policy for an ASG during a scale-in event follows these rules:
1. **Oldest instance**: If the ASG uses multiple instance types, the oldest instances are terminated first.
2. **Instances in the most over-provisioned Availability Zone**: This helps balance the number of instances across zones.
3. **Default termination policy**: Terminate instances in the order specified by the ASG’s termination policy (e.g., oldest first, newest first, or based on instance launch time).

## References
- [What Is Amazon EC2 Auto Scaling?](https://docs.aws.amazon.com/autoscaling/ec2/userguide/what-is-amazon-ec2-auto-scaling.html)
- [Auto Scaling Groups](https://docs.aws.amazon.com/autoscaling/ec2/userguide/AutoScalingGroup.html)
- [AWS Auto Scaling FAQs](https://aws.amazon.com/autoscaling/faqs/)

## Tips
- Use t2.micro instances for the Auto Scaling Group to avoid unexpected charges.
- Don't panic if the instances always come back after you delete them, there's a reason for that.

## Output
![Auto Scaling](https://github.com/user-attachments/assets/588631b8-0178-40b6-aa05-6f06f2c42a71)
