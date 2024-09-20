# STR04-AWS100 - Create an S3 Bucket and store an object in it

## Cloud Service Provider
- Amazon Web Services

## Difficulty
- Level 100 (Introductory)

## Project's Author(s)
- [Syed Auther](https://twitter.com/syedauther)

## Objectives

### You need to complete the following:

- Using the console, create an S3 bucket
- Upload an object (any file) into the bucket

### You need to answer the following:

## What is Simple Storage Service (S3)?

**Amazon S3 (Simple Storage Service)** is an object storage service offered by AWS. It provides scalable, durable, and secure storage for any amount of data, allowing users to store and retrieve data from anywhere. S3 is often used for data backups, media storage, and hosting static websites.

## What is a bucket?

An **S3 bucket** is a logical container used to store objects in Amazon S3. Each bucket is created within a specific AWS region and serves as a namespace for the objects (files, images, backups) stored inside. Buckets have unique names globally across AWS.

## What is object storage?

**Object storage** is a data storage architecture where data is stored as discrete units (objects). Each object contains the data itself, metadata, and a unique identifier. Object storage is ideal for storing unstructured data, such as images, videos, and backups.

## How is object storage different than block storage?

- **Object Storage**: Data is stored as objects, each with metadata and a unique identifier. It's ideal for large, unstructured data like media files and backups. Examples include Amazon S3.
- **Block Storage**: Data is stored in fixed-size blocks, often used in scenarios requiring low-latency access, such as databases or virtual machines. Examples include Amazon EBS (Elastic Block Store).

## What is the maximum amount of data that you can store in an S3 bucket?

There is **no limit** to the amount of data you can store in an S3 bucket. You can store an unlimited number of objects in a bucket, although each object has size restrictions.

## What is the maximum file size you can store in an S3 bucket?

The maximum size for a single object in S3 is **5 TB**. For objects larger than 5 GB, you must use **multipart upload** to upload the object in smaller parts.

## By default, are objects in an S3 bucket public?

No, by default, objects stored in S3 buckets are **private**. Only the bucket owner has access to the objects unless permissions are explicitly granted.

## What are the security best practices regarding S3 buckets?

Here are some best practices for securing S3 buckets:
- **Enable Bucket Policies**: Define explicit permissions for bucket access.
- **Disable Public Access**: Ensure that public access to buckets and objects is blocked unless necessary.
- **Use Encryption**: Encrypt data at rest using AWS KMS or S3-managed keys, and encrypt data in transit using HTTPS.
- **Use IAM Roles and Policies**: Grant access to users or applications using the principle of least privilege.
- **Enable Logging and Monitoring**: Use S3 access logs and AWS CloudTrail to monitor activity and detect suspicious access patterns.

## What is an S3 bucket policy?

An **S3 bucket policy** is a resource-based policy that defines the access permissions for an S3 bucket and its objects. It specifies which users or services can perform actions on the bucket (e.g., `s3:GetObject`, `s3:PutObject`). Bucket policies are written in JSON format and can be used to grant or deny permissions for specific operations.

## What are storage classes in S3?

Amazon S3 offers several **storage classes** designed for different use cases, allowing cost-optimization based on how frequently data is accessed:
- **S3 Standard**: For frequently accessed data.
- **S3 Intelligent-Tiering**: Automatically moves data to lower-cost tiers when access patterns change.
- **S3 Standard-IA (Infrequent Access)**: For less frequently accessed data, but still requires rapid access when needed.
- **S3 One Zone-IA**: For infrequently accessed data stored in a single availability zone.
- **S3 Glacier**: For archival data with retrieval times ranging from minutes to hours.
- **S3 Glacier Deep Archive**: For long-term, rarely accessed data, with retrieval times of 12 to 48 hours.

## How is a bucket policy different from an IAM policy?

- **Bucket Policy**: A resource-based policy applied directly to an S3 bucket, controlling access to the bucket and its objects. It allows cross-account access by granting permissions to specific AWS accounts, users, or roles.
- **IAM Policy**: A user-based policy attached to IAM users, groups, or roles, defining what actions those users can perform on AWS resources, including S3 buckets.

## References
- [Getting Started with S3](https://docs.aws.amazon.com/AmazonS3/latest/gsg/GetStartedWithS3.html)
- [Intro to S3](https://www.youtube.com/watch?v=M_t32mJCXqI)
- [Creating a bucket](https://docs.aws.amazon.com/AmazonS3/latest/gsg/CreatingABucket.html)
- [Uploading your first object into a bucket](https://docs.aws.amazon.com/AmazonS3/latest/gsg/PuttingAnObjectInABucket.html)
- [Bucket Policies](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-policy-language-overview.html)
- [Storage classes in S3](https://aws.amazon.com/s3/storage-classes/)
- [Security breach due to public bucket policies](https://www.bleepingcomputer.com/news/security/540-million-facebook-records-leaked-by-public-amazon-s3-buckets/)

## Costs
- This project is included in the free tier.
- The free tier includes 5GB of Amazon S3 storage in the S3 Standard storage class; 20,000 GET Requests; 2,000 PUT, COPY, POST, or LIST Requests; and 15GB of Data Transfer Out each month.
- An empty bucket does not incur any costs.
- [S3 Pricing after free tier exhaustion](https://aws.amazon.com/s3/pricing/?nc=sn&loc=4)

## Estimated time to complete
- 15 minutes

## Tips
- Each bucket's name has to be unique _globally_, across every single bucket in the world.
- Try to get the URL for the object you uploaded in this task and access it using a browser, you should get an access denied error
- Do not store sensitive information in a bucket that has public access.
- Do not turn on _versioning_ on this bucket, it will be difficult to delete.

## Output 
![image](https://github.com/user-attachments/assets/6a5e60df-0c2e-4762-9062-1827e05694a4)
