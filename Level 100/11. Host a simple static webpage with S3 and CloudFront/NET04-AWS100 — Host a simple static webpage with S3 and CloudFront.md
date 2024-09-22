# NET04-AWS100 — Host a simple static webpage with S3 and CloudFront

## Cloud Service Provider
* Amazon Web Services (AWS)

## Difficulty
Level 100 (Introductory)

## Estimated Time
1 hour

## Project's Author(s)
* [Antonio Lo Fiego](https://twitter.com/antonio_lofiego)

## Objectives

###  You need to complete the following:

* Create an S3 bucket and upload a simple static webpage
* Create a CloudFront distribution and use the S3 bucket as origin
* Make sure that the bucket's content can be accessed only through the CloudFront endpoint

###  You need to answer the following: 

## What is the benefit of using a CDN?

A **Content Delivery Network (CDN)** is a network of distributed servers that cache and deliver content to users based on their geographic location. The benefits of using a CDN include:

- **Improved Performance**: CDNs cache content closer to the end user, reducing latency and improving load times for websites and applications.
- **Scalability**: CDNs can handle large amounts of traffic and sudden spikes in demand, offloading the burden from your origin server.
- **Reliability and Availability**: CDNs provide redundancy and failover capabilities, ensuring content is accessible even if one server or data center experiences issues.
- **Reduced Bandwidth Costs**: CDNs can reduce bandwidth usage and costs by caching content and serving it from their edge locations.
- **Enhanced Security**: CDNs offer features such as DDoS protection, secure data transmission, and Web Application Firewall (WAF) capabilities.

## How would you explain Bucket Policies?

**Bucket Policies** are JSON-based access control policies applied directly to Amazon S3 buckets. They define permissions and rules for accessing the bucket and its objects. Key aspects of bucket policies include:

- **Granular Permissions**: Bucket policies allow you to specify detailed permissions, including which AWS accounts or IAM users can perform actions like reading, writing, or deleting objects.
- **Resource-Based Access Control**: Policies are attached to the bucket itself, enabling cross-account access and more precise control over who can access the bucket.
- **JSON Format**: Policies are written in JSON and include statements that specify actions (e.g., `s3:GetObject`), resources (e.g., bucket and object ARNs), and conditions for access.
- **Examples**: You can use bucket policies to allow public read access, restrict access to certain IP addresses, or allow only specific IAM roles to perform actions on the bucket.

## What are the ways to secure access on a CDN-fronted S3 bucket?

To secure access on an S3 bucket that is fronted by a CDN, you can use the following methods:

1. **Restrict Access with Bucket Policies**:
   - Configure the S3 bucket policy to allow access only from the CDN's edge locations. For example, you can use the `aws:Referer` condition key to restrict access based on specific referrer headers sent by the CDN.

2. **Use Signed URLs**:
   - Generate and use signed URLs to grant temporary access to objects in the S3 bucket. This ensures that only authorized users with valid signed URLs can access the content.

3. **Enable Access Control Lists (ACLs)**:
   - Set ACLs on S3 objects to control access at a more granular level, allowing only specific users or roles to access the objects.

4. **Use Origin Access Identity (OAI)**:
   - If using Amazon CloudFront as your CDN, configure an Origin Access Identity (OAI) to ensure that only CloudFront can access your S3 bucket. This restricts direct access to the bucket, forcing users to go through CloudFront.

5. **Implement HTTPS**:
   - Ensure that all communication between the CDN and the S3 bucket uses HTTPS to protect data in transit from interception or tampering.

6. **Monitor and Audit**:
   - Use AWS CloudTrail and S3 access logs to monitor and audit access requests to the bucket, identifying any unauthorized or suspicious activities.


## References

* [Working with Distributions](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/distribution-working-with.html)
* [Hosting a static website on S3](https://docs.aws.amazon.com/AmazonS3/latest/dev/WebsiteHosting.html)

## Output
![image](https://github.com/shubhammurti/AWS-Projects-Portfolio/blob/5a53cb0b2095ead52a0dd698ab39aceef820d38a/Level%20100/11.%20Host%20a%20simple%20static%20webpage%20with%20S3%20and%20CloudFront/cloudfont.png)
