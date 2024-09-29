# LES01-AWS200 - Create a Serverless API 
## Cloud Service Provider
- Amazon Web Services

## Difficulty
- Level 200 (Intermediate)

## Estimated Time
- One to Two hours. 

## Project's Author(s)

[Syed Auther](https://twitter.com/syedauther)

## Objectives

### You need to complete the following:
- Create an AWS Lambda with a language of your choice, the purpose of this Lambda is to respond with a 'Hello Serverless World!' message.
- Create an API Gateway endpoint and connect it to the AWS Lambda function created above and deploy it as an API that can be consumed from POSTMAN.
- Secure the API with an API Key

### You need to answer the following:

## 1. What is Function as a Service (FaaS)?

**Function as a Service (FaaS)** is a cloud computing model that allows developers to run code in response to events without the need for provisioning or managing servers. It abstracts away server management, enabling developers to focus solely on writing and deploying functions. AWS Lambda is an example of FaaS, where you can execute code based on triggers, such as API Gateway, S3 uploads, or database events.

## 2. How many languages are supported by AWS Lambda?

AWS Lambda natively supports the following programming languages:
- Node.js
- Python
- Ruby
- Java
- Go
- .NET (C#)
- PowerShell
- Custom Runtimes (using AWS Lambda's Runtime API to support other languages)

## 3. What is the maximum memory allocated to an AWS Lambda function?

The maximum memory you can allocate to an AWS Lambda function is **10,240 MB (10 GB)**. Memory can be configured in increments between **128 MB** and **10,240 MB**.

## 4. How many ways to deploy a Lambda function?

There are several ways to deploy a Lambda function, including:
1. **AWS Management Console**: Upload code directly using the console.
2. **AWS CLI (Command Line Interface)**: Deploy using the `aws lambda` command.
3. **AWS SDKs**: Programmatically deploy via supported SDKs.
4. **AWS CloudFormation**: Use Infrastructure as Code (IaC) templates to deploy Lambda functions.
5. **AWS SAM (Serverless Application Model)**: Simplifies the process of deploying serverless applications.
6. **Terraform**: Deploy using Infrastructure as Code (IaC) with Terraform.
7. **CI/CD Pipelines**: Automated deployment using tools like CodePipeline, Jenkins, or GitHub Actions.

## 5. Mention some triggers for AWS Lambda apart from API Gateway

Apart from API Gateway, AWS Lambda can be triggered by a variety of events, including:
- **Amazon S3** (e.g., when an object is uploaded or deleted)
- **Amazon DynamoDB Streams**
- **Amazon SNS (Simple Notification Service)**
- **Amazon SQS (Simple Queue Service)**
- **Amazon CloudWatch Events/Logs**
- **AWS IoT**
- **Amazon Kinesis Streams**

## 6. How to assign a role to AWS Lambda?

To assign a role to an AWS Lambda function:
1. **Create an IAM Role**: Go to the IAM Console, create a role, and assign appropriate permissions (e.g., `AWSLambdaBasicExecutionRole`).
2. **Attach the Role to the Lambda**:
   - Go to the **Lambda Console**.
   - Open your Lambda function.
   - Under the **Configuration** tab, select **Permissions**.
   - Choose the **Execution Role** section, and attach the IAM role you created.

## 7. How many ways to secure an API Gateway endpoint?

You can secure an API Gateway endpoint using various methods, including:
1. **API Keys**: Require API consumers to provide a key to access the API.
2. **AWS IAM Permissions**: Secure the API using IAM roles and policies.
3. **Cognito User Pools**: Use AWS Cognito to authenticate users.
4. **Lambda Authorizers**: Custom authentication logic using Lambda functions.
5. **Usage Plans and Quotas**: Set rate limits and quotas on API access.

## 8. How to add API Gateway as a trigger for AWS Lambda?

To add API Gateway as a trigger for AWS Lambda:
1. **Create a new REST API** or use an existing one in **API Gateway**.
2. Create a **Resource** and a **Method** (e.g., GET or POST).
3. Set the **Integration Type** to **Lambda Function**.
4. Select the Lambda function you want to trigger and deploy the API.
5. Test the API endpoint to ensure it triggers the Lambda function.

## References
- [AWS Lambda- Getting Started](https://aws.amazon.com/lambda/getting-started/)
- [API Gateway Getting Started](https://aws.amazon.com/api-gateway/getting-started/)
- [Connecting AWS Lambda and API Gateway](https://docs.aws.amazon.com/lambda/latest/dg/services-apigateway-tutorial.html)
- [Securing the API](https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-control-access-to-api.html)

## Ideas
- Use a browser to see if the output message 'Hello Serverless World!' is sent back as a response from your Lambda before securing your API. 
- You will need [POSTMAN](https://learning.postman.com/docs/getting-started/introduction/), for testing the API once its secured with an API Key. 
- POSTMAN is not a hard limit, but if you are familiar with any other testing utility you can use that too, but POSTMAN is a good to learn tool, that will come in handy for some other Serverless projects and APIs as well. 

## Tips
- Use the cloud9 IDE to code the hello world Lambda initially, and then explore other deployment ideas like zip file uploads and SAM deployments
- The AWS Lambda free usage tier includes **1M free requests per month and 400,000 GB-seconds of compute time per month**, so feel free to explore unhinged! 

## Output
![image](https://github.com/shubhammurti/AWS-Projects-Portfolio/blob/e8f0ec62608a3287061884e84f1f69aeb452b76a/Level%20200/5.%20Create%20a%20Serverless%20API/Image.png)
