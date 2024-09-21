# LES01-AWS100 - Create a Lambda to add 2 numbers
## Cloud Service Provider
- Amazon Web Services

## Difficulty
- Level 100 (Introductory)

## Estimated Time
- 30 minutes 

## Estimated Cost
- The AWS Lambda free usage tier includes **1M free requests per month and 400,000 GB-seconds of compute time per month**, so feel free to explore unhinged! 

## Project's Author(s)

- [Syed Auther](https://twitter.com/syedauther)

## Objectives

### You need to complete the following:
- Create an AWS Lambda with a language of your choice to add 2 numbers supplied as input and return the result.
- Print the result out in the logs.

### You need to answer the following:
## What is Function as a Service?

**Function as a Service (FaaS)** is a serverless computing model that allows you to run code in response to events without managing servers. It abstracts the infrastructure management away from the developer, enabling you to focus solely on writing and deploying code. AWS Lambda is an example of a FaaS offering that executes code in response to triggers such as HTTP requests, changes in data, or scheduled events.

## How many languages are supported by AWS Lambda?

As of now, AWS Lambda natively supports the following languages:
- **Node.js**
- **Python**
- **Java**
- **Ruby**
- **C# (.NET Core)**
- **Go**
- **PowerShell**

Additionally, Lambda supports custom runtimes, allowing you to use other programming languages by providing your own runtime or using community-supported runtimes.

## What is the maximum memory allocated to an AWS Lambda function?

AWS Lambda allows you to allocate memory from **128 MB to 10,240 MB** (10 GB) in 1 MB increments. The amount of memory allocated impacts the amount of CPU and other resources available to the function.

## How many ways to deploy a Lambda function?

You can deploy an AWS Lambda function in several ways:
1. **AWS Management Console**: Use the web-based interface to create and deploy Lambda functions.
2. **AWS CLI**: Deploy Lambda functions using command-line tools.
3. **AWS SDKs**: Use SDKs to deploy Lambda functions programmatically.
4. **AWS CloudFormation**: Use infrastructure-as-code templates to define and deploy Lambda functions.
5. **AWS SAM (Serverless Application Model)**: A framework for defining and deploying serverless applications using YAML templates.
6. **AWS CDK (Cloud Development Kit)**: Define Lambda functions using high-level programming languages and deploy them using CloudFormation.
7. **Third-party tools**: Deploy using tools like Serverless Framework, Terraform, or others.

## How to write code in the Cloud9 IDE?

To write code in the **AWS Cloud9 IDE**:
1. **Open Cloud9**: Go to the AWS Management Console and open Cloud9 from the Services menu.
2. **Create or open an environment**: Create a new environment or open an existing one.
3. **Access the IDE**: Use the integrated editor to write, edit, and manage your code.
4. **Save and run**: Save your code and use the built-in terminal to run or test your applications directly from the IDE.

## How to test a Lambda function?

You can test an AWS Lambda function in several ways:
1. **AWS Management Console**: Use the built-in test functionality to create test events and execute the function directly from the Lambda dashboard.
2. **AWS CLI**: Use the `aws lambda invoke` command to test the function from the command line.
3. **AWS SDKs**: Invoke the Lambda function programmatically using the SDKs.
4. **Unit Tests**: Write unit tests locally using frameworks appropriate for your programming language, and deploy them to Lambda for further testing.

## What is CloudWatch?

**Amazon CloudWatch** is a monitoring and observability service that provides real-time visibility into the performance and operational health of AWS resources and applications. It collects and tracks metrics, logs, and events, allowing you to monitor, analyze, and respond to changes in your AWS environment.

## How to check the logs for a Lambda function?

To check the logs for an AWS Lambda function:
1. **AWS Management Console**:
   - Go to the CloudWatch Logs section in the AWS Management Console.
   - Find the log group for your Lambda function (usually named `/aws/lambda/<function-name>`).
   - Click on the log group to view log streams and log events.

2. **AWS CLI**:
   - Use the `aws logs` commands to retrieve logs, e.g., `aws logs filter-log-events --log-group-name /aws/lambda/<function-name>`.

3. **CloudWatch Logs Insights**:
   - Use CloudWatch Logs Insights to run queries and analyze log data. 


## References
- [AWS Lambda- Getting Started](https://aws.amazon.com/lambda/getting-started/)
- [AWS Cloudwatch logs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html)
- [Check AWS Lambda logs](https://docs.aws.amazon.com/lambda/latest/dg/monitoring-cloudwatchlogs.html)
- [How to test an AWS Lambda function](https://docs.aws.amazon.com/lambda/latest/dg/getting-started-create-function.html)

## Ideas
- Just create a Lambda function with default settings and choose the language you want to code in, and it give you a starter hello world template , with 2 input parameters event and context,from which event will have the input data that you pass in your test call. 


## Tips
- Use the cloud9 IDE to code the hello world Lambda initially, and then explore other deployment ideas like zip file uploads and SAM deployments

## Output
![image](https://github.com/shubhammurti/AWS-Projects-Portfolio/blob/d13c89d1ac8e21fb366d14bd3bf9883e48fbf8eb/Level%20100/10.%20Create%20a%20Lambda%20to%20add%202%20numbers/lambdafunction.png)
