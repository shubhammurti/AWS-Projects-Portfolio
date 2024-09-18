# COM03-AWS100 - Launch a Hello World website on the internet
## Cloud Service Provider
* Amazon Web Services (AWS)
## Difficulty
Level 100 (Introductory)
## Estimated Time
- 20 minutes 
## Project's Author(s)
* <a href="https://x.com/syedauther">Syed Auther</a>
## Objectives
### You need to complete the following:
* Launch a linux based EC2 instance in any one region of your choice in a public subnet
* Setup a security group that allows http/https connections from the Internet, and ssh from your IP address
* ssh into the EC2 instance
* setup a webserver on the EC2 instance
* add a simple hello world header to the index.html file
* Hit the public IP address from a browser and confirm the site is served
### You need to answer the following:

## 1. What is a Region?
- **Region:** A geographic area that contains multiple data centers (Availability Zones). AWS regions are designed to provide high availability and redundancy.

## 2. What is an Availability Zone?
- **Availability Zone (AZ):** A distinct location within a region that is engineered to be isolated from failures in other Availability Zones. Each AZ is essentially a data center or a group of data centers with its own power, cooling, and networking.

## 3. What is a Public Subnet?
- **Public Subnet:** A subnet within a VPC (Virtual Private Cloud) that has a route to the internet through an Internet Gateway. Resources in a public subnet can directly communicate with the internet.

## 4. How many subnets can there be in one region?
- **Subnets per Region:** There is no hard limit on the number of subnets you can create in a region. However, you are limited by the number of IP addresses available in your VPC's address range and the AWS service quotas.

## 5. How to Launch EC2 Instances in Public/Private Subnets?
- **Public Subnet:** When launching an EC2 instance, choose a public subnet and ensure it has a route to an Internet Gateway.
- **Private Subnet:** Choose a private subnet with no direct route to the internet. Instances in private subnets usually access the internet via a NAT Gateway or NAT Instance located in a public subnet.

## 6. What are AMIs?
- **Amazon Machine Images (AMIs):** Pre-configured templates that contain the operating system, application server, and applications. They serve as a base to launch new EC2 instances.

## 7. What are Security Groups?
- **Security Groups:** Virtual firewalls for your EC2 instances that control inbound and outbound traffic. Security groups operate at the instance level and can be applied to one or more instances.

## 8. What are Inbound/Outbound Rules?
- **Inbound Rules:** Define the allowed incoming traffic to your EC2 instance (e.g., HTTP, HTTPS, SSH).
- **Outbound Rules:** Define the allowed outgoing traffic from your EC2 instance.

## 9. What is the Deny By Default Rule in Security Groups?
- **Deny By Default:** By default, security groups implicitly deny all inbound and outbound traffic unless specific rules are added to allow it. This means no traffic is allowed until explicitly permitted.

## 10. How to Allow Access to EC2 from Security Groups?
- **Allow Access:** Add inbound rules to the security group associated with your EC2 instance to permit specific traffic, such as HTTP (port 80), HTTPS (port 443), or SSH (port 22) from desired IP addresses or CIDR blocks.

## 11. How to Connect to EC2 Instances from Your Machine?
- **SSH Connection:** Use an SSH client to connect to your EC2 instance. Example command:
  ```bash
  ssh -i /path/to/your-key.pem ec2-user@<public-ip-address>

 ## 12. How to Set Up Your Simple Static Site with EC2?
* **Launch EC2 Instance**: Launch an EC2 instance and select a Linux-based AMI.
* **Install Web Server:** SSH into the instance and install a web server (e.g., Apache or Nginx).
* **Deploy Static Site:** Place your static site files (e.g., index.html) in the web server’s root directory (e.g., /var/www/html for Apache).
* **Configure Security Group:** Ensure the security group allows HTTP traffic (port 80) from the internet.
* **Access Site:** Use the instance's public IP address to access your site from a browser.


## References <br />
* <a href="https://aws.amazon.com/ec2/faqs/">What Is Amazon EC2?</a>
* <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html#:~:text=A%20security%20group%20acts%20as,one%20or%20more%20security%20groups.">Security Groups</a>
* <a href="https://httpd.apache.org/docs/2.4/install.html">Installing httpd</a>
* <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/connect-linux-inst-ssh.html">ssh into ec2 - linux</a>

## Ideas
- For windows users [Download and install Putty](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
- Connecting to a Linux EC2 instance from Windows is not possible natively, you will need an ssh client such as Putty to connect , and you will need to follow these steps to [ssh into ec2 from windows](https://stackoverflow.com/questions/5264945/ssh-to-ec2-linux-instance-from-windows)
- You can also launch non linux EC2 instances for example windows servers, for which you will need to RDP into.  

## Costs
- Included in the Free Tier

## Tips
- Use t2.micro instances from the free tier as it will suffice for this static site 
- Use the default setting on the storage screen as 8GB of EBS storage will be enough for this project.


## Output
![Hello World](https://github.com/shubhammurti/AWS-Projects-Portfolio/blob/d08159c41853c633955a27607dc2caa547a861a9/Level%20100/3.%20Launch%20a%20Hello%20World%20website%20on%20the%20internet/hello%20World.png)



