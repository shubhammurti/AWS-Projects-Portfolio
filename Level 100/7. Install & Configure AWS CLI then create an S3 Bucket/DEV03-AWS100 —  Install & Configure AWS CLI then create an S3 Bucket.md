# DEV03-AWS100 —  Install & Configure AWS CLI then create an S3 Bucket

## Cloud Service Provider
* Amazon Web Services (AWS)

## Difficulty
Level 100 (Introductory)

## Estimated Time
* 30 - 40 minutes
  
## Project's Author(s)
* [Ariela](https://twitter.com/ari_hacks)

## Objectives

###  You need to complete the following:

* Create an IAM user with a programmatic access type (and Administrator Access) if you do not have one already
* Install AWS CLI 
* Configure AWS credentials locally: `aws configure` 
* Create an S3 bucket: `aws s3 mb s3://<unique-bucket-name>`
* Check the bucket was created: `aws s3 ls`
* Delete the bucket when you are done: `aws s3 rb s3://<unique-bucket-name>`

###  You need to answer the following: 

## How are permissions granted to IAM users?

Permissions for **IAM (Identity and Access Management)** users are granted through **policies**. These policies define the permissions associated with the user or group. There are two main types of policies:
- **Managed Policies**: AWS-managed or customer-managed policies that can be attached to users, groups, or roles.
- **Inline Policies**: Policies embedded directly within a specific user, group, or role.

IAM users can be assigned one or more policies that specify what AWS resources they can access and the actions they can perform on those resources.

## What credentials are created when configuring AWS locally and where are they stored?

When configuring AWS locally using the `aws configure` command, two types of credentials are typically created:
1. **Access Key ID**: A unique identifier for an AWS user.
2. **Secret Access Key**: A secret key used to sign programmatic requests.

These credentials are stored locally in a file located at:
- **Windows**: `C:\Users\<Username>\.aws\credentials`
- **Linux/macOS**: `~/.aws/credentials`

The configuration file, which stores additional settings like the default region and output format, is located at:
- **Windows**: `C:\Users\<Username>\.aws\config`
- **Linux/macOS**: `~/.aws/config`

## What is the difference between s3 and s3api Commands?

The `aws s3` and `aws s3api` commands provide different levels of interaction with the Amazon S3 service.

- **`aws s3` Commands**:
  - These commands offer higher-level, simplified operations for interacting with Amazon S3. They are often used for basic S3 bucket and object management tasks like uploading files, copying, syncing, listing, and removing objects or directories.
  - **Examples**:
    - `aws s3 cp myfile.txt s3://mybucket/` (copy a file to a bucket)
    - `aws s3 sync /local/dir/ s3://mybucket/` (sync a local directory with an S3 bucket)
  
- **`aws s3api` Commands**:
  - These commands provide low-level access to S3 and expose all available Amazon S3 API operations. They are more granular, allowing users to perform detailed configurations, such as setting bucket policies, tagging, and controlling versioning or logging.
  - **Examples**:
    - `aws s3api create-bucket --bucket mybucket --region us-west-1` (create a new bucket)
    - `aws s3api put-object --bucket mybucket --key myfile.txt --body myfile.txt` (put an object in a bucket)

## References

* [Create an IAM user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html)
* [Install AWS CLI on MacOS](https://docs.aws.amazon.com/cli/latest/userguide/install-macos.html) or with Homebrew:  `brew install awscli` `aws --version`
* [Install AWS CLI on Windows](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-windows.html)
* [Install AWS CLI on Linux](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html)
* [Configure AWS locally](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html)
* [Leveraging the s3 and s3api Commands](https://aws.amazon.com/blogs/developer/leveraging-the-s3-and-s3api-commands/)


## Tips
  - IAM users with programmatic access are given an *access key id* and *secret access key*. After creating a user a *Download.csv* file is generated that contains these values. Download and save the file to access them for setting up AWS locally.

## Output
![image](https://github.com/shubhammurti/AWS-Projects-Portfolio/blob/db0796253f2b26cedfcc6428ae90932d543fbf34/Level%20100/7.%20Install%20%26%20Configure%20AWS%20CLI%20then%20create%20an%20S3%20Bucket/S3.png)
