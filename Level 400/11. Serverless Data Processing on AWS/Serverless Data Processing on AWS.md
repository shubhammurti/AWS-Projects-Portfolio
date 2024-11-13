
## Serverless Data Processing on AWS : AWS Project

### Introduction

In the world of big data, efficient processing and analysis of real-time streams are essential for businesses seeking actionable insights. This project implements a **serverless data processing architecture** using AWS services such as **Amazon Kinesis**, **AWS Lambda**, **Amazon S3**, **Amazon DynamoDB**, **Amazon Cognito**, and **Amazon Athena**. By leveraging these services, the solution can ingest, process, and store data with high scalability and minimal infrastructure management, offering a powerful system for real-time data insights.

### Tech Stack

The serverless solution uses the following AWS services and technologies:

* **AWS Lambda**: Triggers upon events from Kinesis streams, enabling real-time data processing.

* **Amazon Kinesis Data Analytics**: Aggregates and transforms streaming data on the fly.

* **Amazon DynamoDB**: Stores processed data in a fast, scalable NoSQL database.

* **Amazon S3**: Serves as a scalable, durable storage location for raw and processed data.

* **Amazon Kinesis Data Firehose**: Streams raw data directly to S3 for archival and further processing.

* **Amazon Athena**: Allows ad-hoc querying directly on data stored in S3.

* **Amazon Cognito**: Manages user authentication and authorization for secure access to resources.

### Prerequisites

To follow along with this project, ensure you have:

 1. **Basic AWS Knowledge**: Familiarity with Lambda, Kinesis, S3, and IAM services.

 2. **AWS SDKs and CLI**: Installed and configured for command-line interactions with AWS services.

 3. **IAM Permissions**: Set up permissions for Lambda, Kinesis, S3, and DynamoDB.

### Problem Statement or Use Case

A fictive company [Wild Rydes](http://wildrydes.com/) introduces an innovative transportation service that offers unicorn rydes to help people to get to their destination faster and hassle-free. Each unicorn is equipped with a sensor that reports its location and vital signs. During this workshop, we’ll build infrastructure to enable operations personnel at Wild Rydes to monitor the health and status of their unicorn fleet. We’ll use AWS to build applications that process and visualize the unicorn data in real-time.

## Architecture Diagram

Below is a visual representation of the serverless data processing architecture, showing data flow from ingestion through Kinesis, processing with Lambda, and storage in DynamoDB and S3.

![](https://cdn-images-1.medium.com/max/5284/1*uD26r0KzxfzWN5AvrKZ5zw.png)

### Component Breakdown

 1. **Amazon Kinesis Data Streams**: Collects data from various sources, enabling the flow of real-time data.

 2. **AWS Lambda**: Processes data in real-time when triggered by Kinesis events, transforming the data before it’s stored.

 3. **Amazon Kinesis Data Analytics**: Provides on-the-fly data aggregation and transformation to gain insights before storage.

 4. **Amazon DynamoDB**: Stores processed data for fast retrieval, especially suitable for structured data.

 5. **Amazon S3**: Holds raw data and processed datasets, ensuring durability and scalability.

 6. **Amazon Kinesis Data Firehose**: Streams data directly to S3 for long-term storage and archiving.

 7. **Amazon Athena**: Allows for ad-hoc querying on the data stored in S3, ideal for data analysis without data movement.

 8. **Amazon Cognito**: Ensures secure user authentication, managing permissions and access control.

## Step-by-Step Implementation

## AWS Cloud9 IDE

[AWS Cloud9](https://aws.amazon.com/cloud9/) is a cloud-based integrated development environment (IDE) that lets you write, run, and debug your code with just a browser. It includes a code editor, debugger, and terminal. Cloud9 comes pre-packaged with essential tools for popular programming languages and the AWS Command Line Interface (CLI) pre-installed so you don’t need to install files or configure your laptop for this workshop. Your Cloud9 environment will have access to the same AWS resources as the user with which you logged into the AWS Management Console.

Take a moment now and setup your Cloud9 development environment.

✅ Step-by-step Instructions

 1. Go to the AWS Management Console, click Services then select Cloud9 under Developer Tools.

 2. Click Create environment.

 3. Enter Development into Name and optionally provide a Description.

 4. Click Next step.

 5. You may leave Environment settings at their defaults of launching a new t2.micro EC2 instance which will be paused after 30 minutes of inactivity.

 6. Click Next step.

 7. Review the environment settings and click Create environment. It will take several minutes for your environment to be provisioned and prepared.

 8. Once ready, your IDE will open to a welcome screen. Below that, you should see a terminal prompt similar to:

![](https://cdn-images-1.medium.com/max/2000/0*dqNdu3KDLpEy-6KL.png)

If you are running this workshop at an AWS event: Paste here the Credentials/CLI Snippets you copied before to configure your environment with your credentials. If you are running it in your own account, you can use the default profile Cloud9 sets up for you. You can check it via cat ~/.aws/credentials.

![](https://cdn-images-1.medium.com/max/3476/0*6wlBopjlDFXNhKnl.png)

Now you can run AWS CLI commands in here just like you would on your local computer. Verify that your user is logged in by running aws sts get-caller-identity.

    aws sts get-caller-identity

You’ll see output indicating your account and user information:

    Admin:~/environment $ aws sts get-caller-identity

    {
        "Account": "123456789012",
        "UserId": "AKIAI44QH8DHBEXAMPLE",
        "Arn": "arn:aws:iam::123456789012:user/Alice"
    }

Keep your AWS Cloud9 IDE opened in a tab throughout this workshop as you’ll use it for activities like building and running a sample app in a Docker container and using the AWS CLI.

## Command Line Clients

The modules utilize two command-line clients to simulate and display sensor data from the unicorns in the fleet. These are small programs written in the [Go Programming Language](https://golang.org/). The below instructions in the [Installation](https://data-processing.serverlessworkshops.io/setup/03-cloud9-setup.html#installation) section walks through downloading pre-built binaries, but you can also download the source and build it manually:

* [producer.go](https://data-processing.serverlessworkshops.io/client/producer.go)

* [consumer.go](https://data-processing.serverlessworkshops.io/client/consumer.go)

### Producer

The producer generates sensor data from a unicorn taking a passenger on a Wild Ryde. Each second, it emits the location of the unicorn as a latitude and longitude point, the distance traveled in meters in the previous second, and the unicorn’s current level of magic and health points.

### Consumer

The consumer reads and displays formatted JSON messages from an Amazon Kinesis stream which allow us to monitor in real-time what’s being sent to the stream. Using the consumer, you can monitor the data the producer and your applications are sending.

### Installation

 1. Switch to the tab where you have your Cloud9 environment opened.

 2. Download and unpack the command line clients by running the following command in the Cloud9 terminal:

* curl -s https://data-processing.serverlessworkshops.io/client/client.tar | tar -xv

This will unpack the consumer and producer files to your Cloud9 environment.

## ⭐ Tips

💡 Keep an open scratch pad in Cloud9 or a text editor on your local computer for notes. When the step-by-step directions tell you to note something such as an ID or Amazon Resource Name (ARN), copy and paste that into the scratch pad.

## ⭐ Recap

🔑 Use a unique personal, development [AWS Account](https://data-processing.serverlessworkshops.io/setup/02-self-paced.html#self_paced), [event engine](https://data-processing.serverlessworkshops.io/setup/01-at-aws-event.html#event_engine) or [EventBox](https://data-processing.serverlessworkshops.io/setup/01-at-aws-event.html#event_box)

🔑 Use one of the US East (N. Virginia), US West (Oregon), EU* (Ireland, London, Frankfurt) [Regions](https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/) if using your own AWS account.

🔑 Keep your [AWS Cloud9 IDE](https://data-processing.serverlessworkshops.io/setup/03-cloud9-setup.html#aws-cloud9-ide) opened in a tab

## Real-time Data Streaming

In this module, you’ll create an Amazon Kinesis stream to collect and store sensor data from our unicorn fleet. Using the provided command-line clients, you’ll produce sensor data from a unicorn on a Wild Ryde and read from the stream. Lastly, you’ll use the unicorn dashboard to plot our unicorns on a map and watch their status in real-time. In subsequent modules you’ll add functionality to analyze and persist this data using Amazon Kinesis Data Analytics, AWS Lambda, and Amazon DynamoDB.

## Overview

The architecture for this module involves an Amazon Kinesis stream, a producer, and a consumer.

Our producer is a sensor attached to a unicorn currently taking a passenger on a ride. This sensor emits data every second including the unicorn’s current location, distance traveled in the previous second, and magic points and hit points so that our operations team can monitor the health of the unicorn fleet from Wild Rydes headquarters.

The Amazon Kinesis stream stores data sent by the producer and provides an interface to allow consumers to process and analyze those data. Our consumer is a simple command-line utility that tails the stream and outputs the data points from the stream in effectively real-time so we can see what data is being stored in the stream. Once we send and receive data from the stream, we can use the [unicorn dashboard](https://data-processing.serverlessworkshops.io/dashboard.html) to view the current position and vitals of our unicorn fleet in real-time.

![](https://cdn-images-1.medium.com/max/4000/0*sDUVAwqA3sElJh5R.jpg)

## Implementation

❗ Ensure you’ve completed the [setup guide](https://data-processing.serverlessworkshops.io/setup.html) before beginning the workshop.

### 1. Create an Amazon Kinesis stream

Use the Amazon Kinesis Data Streams console to create a new provisioned stream named wildrydes with 1 shard.

A Shard is the base throughput unit of an Amazon Kinesis data stream. One shard provides a capacity of 1MB/sec data input and 2MB/sec data output. One shard can support up to 1000 PUT records per second. You will specify the number of shards needed when you create a data stream. For example, if we create a data stream with four shards then this data stream has a throughput of 4MB/sec data input and 8MB/sec data output, and allows up to 4000 PUT records per second. You can monitor shard-level metrics in Amazon Kinesis Data Streams and add or remove shards from your data stream dynamically as your data throughput changes by resharding the data stream.

At re:Invent 2021, AWS introduced a new capacity mode for Kinesis Data Streams called [Kinesis Data Streams On-Demand](https://aws.amazon.com/about-aws/whats-new/2021/11/amazon-kinesis-data-streams-on-demand/). The new mode is capable of serving gigabytes of write and read throughput per minute without capacity planning. During this workshop, we will use the provisioned mode with shard capacity planning for educational purposes. For your environments, you should consider using on-demand capacity mode based on your needs and cost considerations.

✅ Step-by-step Instructions

 1. Go to the [AWS Management Console](https://console.aws.amazon.com/), click Services then select Kinesis under Analytics.

 2. Click Get started if prompted with an introductory screen.

 3. Click Create data stream.

 4. Enter wildrydes into Kinesis stream name

 5. Select the Provisioned option and enter 1 into Number of shards, then click Create Kinesis stream.

 6. Within 60 seconds, your Kinesis stream will be ACTIVE and ready to store real-time streaming data.

![](https://cdn-images-1.medium.com/max/2944/0*6z6-yLcLm1g4Rqvr.png)

### 2. Produce messages into the stream

Use the [command-line producer](https://data-processing.serverlessworkshops.io/setup.html#producer) to produce messages into the stream.

✅ Step-by-step Instructions

 1. Switch to the tab where you have your Cloud9 environment opened.

 2. In the terminal, run the producer to start emitting sensor data to the stream.

* ./producer

 1. The producer emits a message a second to the stream and prints a period to the screen.

* $ ./producer ..................................................

 1. In the Amazon Kinesis Streams console, click on wildrydes and click on the Monitoring tab.

 2. After several minutes, you will see the Put Record Success (percent) — Average graph begin to record a single put a second. Keep the producer running till end of the Lab 2, so that you can see the unicorns flying in action.

### 3. Read messages from the stream

✅ Step-by-step Instructions

 1. While the producer is running, switch to the tab where you have your Cloud9 environment opened.

 2. Hit the (+) button and click New Terminal to open a new terminal tab.

 3. Run the consumer to start reading sensor data from the stream.

* ./consumer

 1. The consumer will print the messages being sent by the producer:

* { "Name": "Shadowfax", "StatusTime": "2017-06-05 09:17:08.189", "Latitude": 42.264444250051326, "Longitude": -71.97582884770408, "Distance": 175, "MagicPoints": 110, "HealthPoints": 150 } { "Name": "Shadowfax", "StatusTime": "2017-06-05 09:17:09.191", "Latitude": 42.265486935100476, "Longitude": -71.97442977859625, "Distance": 163, "MagicPoints": 110, "HealthPoints": 151 }

### 4. Create an identity pool for the unicorn dashboard

Create an Amazon Cognito identity pool to grant unauthenticated users access to read from your Kinesis stream. Note the identity pool ID for use in the next step.

✅ Step-by-step directions

 1. Go to the AWS Management Console, click Services then select Cognito under Security, Identity & Compliance.

 2. Click Manage Identity Pools.

 3. Click Create new identity pool. [This is not necessary if you do not have any identity pool yet.]

 4. Enter wildrydes into Identity pool name.

 5. Tick the Enable access to unauthenticated identities checkbox.

 6. Click Create Pool.

 7. Click Allow which will create authenticated and unauthenticated roles for your identity pool.

 8. Click Go to Dashboard.

 9. Click Edit identity pool in the upper right hand corner.

 10. Note the Identity pool ID for use in a later step.

![](https://cdn-images-1.medium.com/max/3632/0*CIrDt5MP4ID7oFbT.png)

### 5. Grant the unauthenticated role access to the stream

Add a new policy to the unauthenticated role to allow the dashboard to read from the stream to plot the unicorns on the map.

✅ Step-by-step directions

 1. Go to the AWS Management Console, click Services then select IAM under Security, Identity & Compliance.

 2. Click on Roles in the left-hand navigation.

 3. Click on the Cognito_wildrydesUnauth_Role.

 4. Click Add inline policy (Add permissions -> Create inline policy).

 5. Click on Choose a service and click Kinesis.

 6. Click on Actions.

 7. Tick the Read and List permissions checkboxes.

 8. Under Resources you will limit the role to the wildrydes stream and consumer.

 9. Click Add ARN next to consumer.

 10. In the Add ARN(s) dialog box, enter the following information:

* the region you’re using in Region (e.g. us-east-1)

* your [Account ID](https://docs.aws.amazon.com/IAM/latest/UserGuide/console_account-alias.html) in Account

* * in Stream type

* wildrydes in Stream name

* * in Consumer name

* * in Consumer creation timestamp

 1. Click Add.

 2. Click Add ARN next to stream.

 3. In the Add ARN(s) dialog box, enter the following information:

* the region you’re using in Region (e.g. us-east-1)

* your [Account ID](https://docs.aws.amazon.com/IAM/latest/UserGuide/console_account-alias.html) in Account

* wildrydes in Stream name

 1. Click Add.

![](https://cdn-images-1.medium.com/max/3864/0*YYhCoY5eKHjsucKx.png)

 1. Click Review policy.

 2. Enter WildrydesDashboardPolicy in Name.

 3. Click Create policy.

### 6. View unicorn status on the dashboard

Use the [Unicorn Dashboard](https://data-processing.serverlessworkshops.io/dashboard.html) to see the unicorn on a real-time map. You may need to zoom out to find the unicorn. Please double check that producer and consumer are both running if you can’t find it.

✅ Step-by-step directions

 1. Open the [Unicorn Dashboard](https://data-processing.serverlessworkshops.io/dashboard.html).

 2. Enter the Cognito Identity Pool ID you noted in step 4 and click Start.

![](https://cdn-images-1.medium.com/max/2000/0*2b_AESSzu_pNuFAI.png)

 1. Validate that you can see the unicorn on the map.If you can not see the unicorn, please go back to Cloud9 and run ./producer.

![](https://cdn-images-1.medium.com/max/2000/0*SiBkpp6D7xVxuFnY.png)

 1. Click on the unicorn to see more details from the stream and compare with the consumer output.

![](https://cdn-images-1.medium.com/max/2100/0*1uvBnj3fU2TU-pz6.png)

The speed is calculated internally based on the difference of the longitude and latitude values.

### 7. Experiment with the producer

Stop and start the producer while watching the dashboard and the consumer. Start multiple producers with different unicorn names.

 1. Stop the producer by pressing Control + C and notice the messages stop and the unicorn disappear after 30 seconds.

 2. Start the producer again and notice the messages resume and the unicorn reappear.

 3. Hit the (+) button and click New Terminal to open a new terminal tab.

 4. Start another instance of the producer in the new tab. Provide a specific unicorn name and notice data points for both unicorns in consumer’s output:

* ./producer -name Bucephalus

 1. Check the dashboard and verify you see multiple unicorns.

![](https://cdn-images-1.medium.com/max/2000/0*b6Rd5DDoUC7InMQf.png)

## ⭐ Recap

🔑 Amazon Kinesis makes it easy to collect, process, and analyze real-time, streaming data so you can get timely insights and react quickly to new information.

🔧 In this module, you’ve created an Amazon Kinesis stream and used it to store and visualize data from a simulated fleet of unicorns.

## Stream Processing and analytics with AWS Lambda

## Stream Processing and analytics with AWS Lambda

In this module, you’ll use [AWS Lambda](https://aws.amazon.com/lambda/) to process data from the wildrydes [Amazon Kinesis stream](https://aws.amazon.com/kinesis/data-streams/) created earlier. We’ll create and configure a Lambda function to read from the stream and write records to an [Amazon DynamoDB](https://aws.amazon.com/dynamodb) table as they arrive. We will also explore a few error handling mechanisms when there are poison pill messages in the stream. Finally, We will learn how to do stream analytics with AWS Lambda.

Our target architecture looks as follows:

![](https://cdn-images-1.medium.com/max/3540/0*xcWLGER68HqY3oMz.png)

## Setup

## Implementation

In this module, you’ll setup all of the resources needed to support processing records from the Kinesis Data Stream wildrydes including a Dynamo DB table, a Lambda function, an IAM role, a Kinesis Data Stream, and a SQS queue.

Resources

 1. [Create a Dynamo DB Table](https://data-processing.serverlessworkshops.io/stream-processing/01-setup.html#create_dynamo_db_table)

 2. [Create an SQS On-Error Destination Queue](https://data-processing.serverlessworkshops.io/stream-processing/01-setup.html#create_sqs_dlq)

 3. [Create an IAM Role](https://data-processing.serverlessworkshops.io/stream-processing/01-setup.html#create_iam_role)

 4. [Create a Lambda Function](https://data-processing.serverlessworkshops.io/stream-processing/01-setup.html#create_lambda)

### 1. Create an Amazon DynamoDB table

Use the [Amazon DynamoDB](https://console.aws.amazon.com/dynamodbv2/home) console to create a new DynamoDB table. This table is used to store the unicorn data from the AWS Lambda function. We will call your table UnicornSensorData and give it a Partition key called Name of type String and a Sort key called StatusTime of type String. Use the defaults for all other settings.

After you’ve created the table, note the Amazon Resource Name (ARN) for use in the next section.

✅ Step-by-step Instructions

 1. Go to the AWS Management Console, choose Services then select DynamoDB under Database. Alternatively, you can use the search bar and type DynamoDB in the search dialog box.

 2. Click Create table.

 3. Enter UnicornSensorData for the Table name.

 4. Enter Name for the Partition key and select String for the key type.

 5. Enter StatusTime for the Sort key and select String for the key type.

 6. Leave the Use default settings box checked and choose Create.

![](https://cdn-images-1.medium.com/max/3392/0*g8f99dzKwxgkKgFd.png)

 1. Once the table is created, Click on the hyperlink on the table name. This will take you to the new screen. Under General information, You will see Amazon Resource Name (ARN). Copy and save the Amazon Resource Name (ARN) in the scratchpad. You will use this when creating IAM role.

### 2. Create an SQS On-Error Destination Queue

Use the [Amazon SQS](https://console.aws.amazon.com/sqs) console to create a new queue nammed wildrydes-queue. Your Lambda function will send messages to this queue when the processing is failed based on the retry settings.

After you’ve created the queue, note the Amazon Resource Name (ARN) for use in later sections.

✅ Step-by-step Instructions

 1. Go to the AWS Management Console, choose Services then select Simple Queue Service under Application Integration. Alternatively, you can use the search bar and type Simple Queue Service in the search dialog box.

 2. Click the orange Create queue button

 3. For the Name field enter wildrydes-queue

 4. Leave the rest of the options as the defaults and click “Create queue”

![](https://cdn-images-1.medium.com/max/2584/0*7DpT6G4vsVEaqQe1.png)

 1. Copy and save the ARN of the SQS queue in the scratchpad as you will need it for Lambda configuration

### 3. Create an IAM role for your Lambda function

Use the [IAM](https://console.aws.amazon.com/iamv2/home) console to create a new role. Name it WildRydesStreamProcessorRole and select Lambda for the role type. Create a policy that allows dynamodb:BatchWriteItem access to the DynamoDB table created in the last section and sqs:SendMessage to send failed messages to DLQ and attach it to the new role. Also, Attach the managed policy called AWSLambdaKinesisExecutionRole to this role in order to grant permissions for your function to read from Amazon Kinesis streams and to log to Amazon CloudWatch Logs.

✅ Step-by-step Instructions

 1. From the AWS Console, click on Services and then select IAM in the Security, Identity & Compliance section. Alternatively, you can use the search bar and type IAM in the search dialog box.

 2. Select Policies from the left navigation and then click Create policy.

 3. Using the Visual editor, we’re going to create an IAM policy to allow our Lambda function access to the DynamoDB table created in the last section. To begin, click Service, begin typing DynamoDB in Find a service, and click DynamoDB.

 4. Click Action, begin typing BatchWriteItem in Filter actions, and tick the BatchWriteItem checkbox.

 5. Click Resources, click Add ARN in table, Copy the ARN of the DyanamoDB table from the scratchpad and paste it in Specify ARN for table. Alternatively, you can construct the ARN of the DynamoDB table you created in the previous section by specifying the Region, Account, and Table Name.

 6. In Region, enter the AWS Region in which you created the DynamoDB table in the previous section, e.g.: us-east-1.

 7. In Table Name, enter UnicornSensorData.

 8. You should see your ARN in the Specify ARN for table field and it should look similar to:

![](https://cdn-images-1.medium.com/max/2000/0*lfXLh1RAfp7s7Q8j.png)

 1. Click Add.

 2. When completed, your console should look similar to this:

![](https://cdn-images-1.medium.com/max/2982/0*7vBc-WY7KUSeVex2.png)

 1. Next we are going to add permissions to allow the Lambda function access to the SQS On-Error Destination Queue. Click Add additional permissions click Service begin typing SQS in Find a service and click SQS.

 2. Click Action begin typing SendMessage in Filter actions, and tick the SendMessage checkbox.

 3. Click Resources, click Add ARN in queue. Copy the ARN of the SQS queue from the scratchpad and paste it in Specify ARN for queue. Alternatively, you can construct the ARN of the SQS queue you created in the previous section by specifying the Region, Account, and Queue Name.

* In **Region**, enter the AWS Region in which you created the SQS queue in the previous section, e.g.: us-east-1. In **Queue Name**, enter `wildrydes-queue`. You should see your ARN in the **Specify ARN for queue** field and it should look similar to: ![](./images/01-iam-policy-sqs.png)

 1. Click Next: Tags**.

 2. Click Next: Review**.

 3. Enter WildRydesDynamoDBWritePolicy in the Name field.

 4. Click Create policy.

 5. Select Roles from the left navigation and then click Create role.

 6. Click Lambda for the role type from the AWS service section.

 7. Click Next: Permissions.

 8. Begin typing AWSLambdaKinesisExecutionRole in the Filter text box and check the box next to that role.

 9. Begin typing WildRydesDynamoDBWritePolicy in the Filter text box and check the box next to that policy.

 10. Click Next.

 11. Enter WildRydesStreamProcessorRole for the Role name.

 12. Click Create role.

 13. Begin typing WildRydesStreamProcessorRole in the Search text box

![](https://cdn-images-1.medium.com/max/4000/0*2TZWeL_41mHUQJnl.png)

 1. Click on WildRydesStreamProcessorRole and it should look similar to:

![](https://cdn-images-1.medium.com/max/2812/0*Fesl7dUn1sAJTdbU.png)

### 4. Create a Lambda function to process the stream

Create a Lambda function called WildRydesStreamProcessor that will be triggered whenever a new record is avaialble in the wildrydes stream. Use the provided index.js implementation for your function code. Create an environment variable with the key TABLE_NAME and the value UnicornSensorData. Configure the function to use the WildRydesStreamProcessor role created in the previous section.

✅ Step-by-step Instructions

 1. Go to the AWS Management Console, choose Services then select Lambda under Compute. Alternatively, you can use the search bar and type Lambda in the search dialog box.

 2. Click Create function.

 3. Enter WildRydesStreamProcessor in the Function name field.

 4. Select Node.js 14.x from Runtime.

 5. Select WildRydesStreamProcessorRole from the Existing role dropdown.

![](https://cdn-images-1.medium.com/max/4000/0*HNtWxs9bm8C2zVg6.png)

 1. Click Create function.

 2. Scroll down to the Code source section.

 3. Copy and paste the JavaScript code below into the code editor.

* "use strict"; const AWS = require("aws-sdk"); const dynamoDB = new AWS.DynamoDB.DocumentClient(); const tableName = process.env.TABLE_NAME; // Entrypoint for Lambda Function exports.handler = function (event, context, callback) { const requestItems = buildRequestItems(event.Records); const requests = buildRequests(requestItems); Promise.all(requests) .then(() => callback(null, `Delivered ${event.Records.length} records`) ) .catch(callback); }; // Build DynamoDB request payload function buildRequestItems(records) { return records.map((record) => { const json = Buffer.from(record.kinesis.data, "base64").toString( "ascii" ); const item = JSON.parse(json); return { PutRequest: { Item: item, }, }; }); } function buildRequests(requestItems) { const requests = []; // Batch Write 25 request items from the beginning of the list at a time while (requestItems.length > 0) { const request = batchWrite(requestItems.splice(0, 25)); requests.push(request); } return requests; } // Batch write items into DynamoDB table using DynamoDB API function batchWrite(requestItems, attempt = 0) { const params = { RequestItems: { [tableName]: requestItems, }, }; let delay = 0; if (attempt > 0) { delay = 50 * Math.pow(2, attempt); } return new Promise(function (resolve, reject) { setTimeout(function () { dynamoDB .batchWrite(params) .promise() .then(function (data) { if (data.UnprocessedItems.hasOwnProperty(tableName)) { return batchWrite( data.UnprocessedItems[tableName], attempt + 1 ); } }) .then(resolve) .catch(reject); }, delay); }); }

![](https://cdn-images-1.medium.com/max/3682/0*74ZRG4Pm0yQK3Bp7.png)

 1. Now, You will be adding the DynamoDB table name as an environment variable. In the Configuration tab, select the Environment variables section.

![](https://cdn-images-1.medium.com/max/2706/0*T3lEGpz4--cE2DIM.png)

 1. Click Edit and then Add environment variable

* Enter TABLE_NAME in Key and UnicornSensorData in Value.

* Add another environment variable called AWS_NODEJS_CONNECTION_REUSE_ENABLED in Key and 1 in Value. This setting helps to reuse TCP connection. You can learn more [here](https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/node-reusing-connections.html)

* click Save.

 1. Now, You will add the event source mapping(ESM) for AWS Lambda to integrate with Kinesis. Scroll up and click on Add Trigger from the Function overview section.

![](https://cdn-images-1.medium.com/max/2000/0*0uPfmTpu3skiblhD.png)

 1. In the Trigger configuration section, select Kinesis.

 2. Select wildrydes from Kinesis stream.

 3. Leave Batch size set to 100 and Starting position set to Latest.

 4. Open the Additional settings section

 5. Under On-failure destination add the ARN of the wildrydes-queue SQS queue

 6. Make sure Enable trigger is checked.

 7. Click Add.

![](https://cdn-images-1.medium.com/max/2000/0*YpmWtSQmpcAz0Iip.png)

 1. Go back to Code Tab and Deploy the Lambda function — the screen will provide a message on successful deployment.

![](https://cdn-images-1.medium.com/max/2050/0*D7BD7sWFyddglIUn.png)

## ⭐ Recap

🔑 You can subscribe Lambda functions to automatically read batches of records off your Kinesis stream and process them if records are detected on the stream.

🔧 In this module, you’ve setup a DynamoDB table for storing unicorn data, a Dead Letter Queue(DLQ) for recieving failed messages and a Lambda function to read data from Kinesis Data Stream and store in DynamoDB.

## Stream Processing

## Implementation

In the [SetUp](https://data-processing.serverlessworkshops.io/stream-processing/01-setup.html) section, we set up the all the necessary services and roles required to read a message from Amazon Kinesis Data Stream wildrydes by the Lambda function WildRydesStreamProcessor. This function processes the records and inserts the data into Amazon DynamoDB table UnicornSensorData.

Lambda reads records from the data stream and invokes your function synchronously with an event that contains stream records. Lambda reads records in batches and invokes your function to process records from the batch. Each batch contains records from a single shard/data stream. Follow this [link](https://docs.aws.amazon.com/lambda/latest/dg/with-kinesis.html) to learn more about this integration

In this module, you’ll send streaming data to Amazon Kinesis Data Stream, wildrydes using the producer.go library and use the AWS Console to monitor Lambda’s processing of records from the wildrydes stream and query the results in Amazon DynamoDB.

### 1. Produce streaming data

 1. Return to you AWS Cloud9 instance and run the producer to start emitting sensor data to the stream with a unique unicorn name.

* ./producer -name Shadowfax -stream wildrydes -msgs 20

### 2. Verify Lambda execution

Verify that the trigger is properly executing the Lambda function. View the metrics emitted by the function and inspect the output from the Lambda function.

✅ Step-by-step Instructions

 1. Return to the AWS Lambda function console. Click on the Monitor tab and explore the metrics available to monitor the function.

![](https://cdn-images-1.medium.com/max/2694/0*uaMSYvpSjCkGaNFB.png)

 1. Click on Logs to explore the function’s log output.

![](https://cdn-images-1.medium.com/max/2704/0*mADGOW2p6ikFWWVW.png)

 1. Click on View logs in CloudWatch to explore the logs in CloudWatch for the log group /aws/lambda/WildRydesStreamProcessor

![](https://cdn-images-1.medium.com/max/2050/0*yOKa5Z-B2D7c5s1s.png)

The log groups can take a while to create so if you see “Log Group Does Not Exist” when pressing “View Logs” in CloudWatch then just wait a few more minutes before hitting refresh.

### 3. Query the DynamoDB table

Using the AWS Management Console, query the DynamoDB table for data for a specific unicorn. Use the producer to create data from a distinct unicorn name and verify those records are persisted.

✅ Step-by-step Instructions

 1. Click on Services then select DynamoDB in the Database section.

 2. Click Tables from the left-hand navigation

 3. Click on UnicornSensorData.

 4. Click on the Explore table items button at the top right. Here you should see the Unicorn data for which you’re running a producer.

![](https://cdn-images-1.medium.com/max/3920/0*Ern-btJLesd7YUMi.png)

By default, There is one to one mapping between Kinesis shard to Lambda function invocation. You can configure the ParallelizationFactor setting to process one shard of a Kinesis with more than one Lambda invocation simultaneously. If you increase the number of concurrent batches per shard, Lambda still ensures in-order processing at the partition-key level. Follow the [link](https://aws.amazon.com/blogs/compute/new-aws-lambda-scaling-controls-for-kinesis-and-dynamodb-event-sources/) to learn more about parallelization.

## ⭐ Recap

🔑 You can subscribe Lambda functions to automatically read batches of records off your Kinesis stream and process them if records are detected on the stream.

🔧 In this module, you’ve created a Lambda function that reads from the Kinesis Data Stream wildrydes and saves each row to DynamoDB.

## Error Handling

## Implementation

In this module, you’ll setup AWS Lambda to process data and handle errors when processing data from the wildrydes created earlier. There are couple of approaches for error handling.

Resources

 1. [Error Handling with Retry Settings](https://data-processing.serverlessworkshops.io/stream-processing/03-error-handling.html#error_handling_with_retry)

 2. [Error Handling with Bisect On Batch](https://data-processing.serverlessworkshops.io/stream-processing/03-error-handling.html#error_handling_with_bisect_on_batch)

### 1. Error Handling with Retry Settings

AWS Lambda can reprocess batches of messages from Kinesis Data Streams when an error occurs in one of the items in the batch. You can configure the number of retries by configuring Retry attempts and/or Maximum age of record. The batch will be retried until the number of retry attempts or until the expiration of the batch. You can also configure On-failure destination which will be used by Lambda to send metadata of your failed invocation. You can send this metadata of the failed invocation to either an Amazon SQS queue or an Amazon SNS topic. Typically there are two kinds of errors in the data stream. One category belongs to transient errors which are temporary in nature and are successfully processed with retry logic. Second category belongs to Poison Pill (either data quality / data that generates an exception in Lambda code) which are permanent in nature. In this case Lambda retries for the configured retry attempts and then discards the records to the On-failure destination.

In order to simulate poison pill message, We will introduce an error data in streaming data and throw an error when it is found in the message. In real world, this may be a validation or a call to another service which expects certain information in the record. This is the code change that will be introduced in the Lambda function

    if (item.InputData.toLowerCase().includes(errorString)) {
        console.log("Error record is = ", item);
        throw new Error("kaboom");
    }

✅ Step-by-step Instructions

 1. Go to the AWS Management Console, choose Services then select Lambda under Compute. Alternatively, you can use the search bar and type Lambda in the search dialog box.

 2. Click the WildRydesStreamProcessor function

 3. Scroll down to the Function Code section.

 4. Double click the index.js file to open it in the editor

 5. Copy and paste the JavaScript code below into the code editor, replacing all of the existing code.

* "use strict"; const AWS = require("aws-sdk"); const dynamoDB = new AWS.DynamoDB.DocumentClient(); const tableName = process.env.TABLE_NAME; // This is used to mimic poison pill messages const errorString = "error"; // Entrypoint for Lambda Function exports.handler = function (event, context, callback) { console.log( "Number of Records sent for each invocation of Lambda function = ", event.Records.length ); const requestItems = buildRequestItems(event.Records); const requests = buildRequests(requestItems); Promise.all(requests) .then(() => callback(null, `Delivered ${event.Records.length} records`) ) .catch(callback); }; // Build DynamoDB request payload function buildRequestItems(records) { return records.map((record) => { const json = Buffer.from(record.kinesis.data, "base64").toString( "ascii" ); const item = JSON.parse(json); //Check for error and throw the error. This is more like a validation in your usecase if (item.InputData.toLowerCase().includes(errorString)) { console.log("Error record is = ", item); throw new Error("kaboom"); } return { PutRequest: { Item: item, }, }; }); } function buildRequests(requestItems) { const requests = []; // Batch Write 25 request items from the beginning of the list at a time while (requestItems.length > 0) { const request = batchWrite(requestItems.splice(0, 25)); requests.push(request); } return requests; } // Batch write items into DynamoDB table using DynamoDB API function batchWrite(requestItems, attempt = 0) { const params = { RequestItems: { [tableName]: requestItems, }, }; let delay = 0; if (attempt > 0) { delay = 50 * Math.pow(2, attempt); } return new Promise(function (resolve, reject) { setTimeout(function () { dynamoDB .batchWrite(params) .promise() .then(function (data) { if (data.UnprocessedItems.hasOwnProperty(tableName)) { return batchWrite( data.UnprocessedItems[tableName], attempt + 1 ); } }) .then(resolve) .catch(reject); }, delay); }); }

 1. Click Deploy to deploy the changes to the WildRydesStreamProcessor Lambda function.

 2. Remove the existing Kinesis Data Stream mapping by clicking the Configuration Tab above the code editor. (This step is needed only if there is an existing Kinesis Data Stream mapping or any other Event Source Mapping present for the Lambda function). In the Configuration Tab, Select the Kinesis:wildrydes (Enabled). If the trigger is not enabled, press refresh. Delete the trigger.

![](https://cdn-images-1.medium.com/max/3414/0*70D976z3UjU0sS16.png)

 1. Add a new Kinesis Data Stream mapping by clicking the Configuration Tab.

 2. Select the Triggers section and Add trigger button.

 3. Select Kinesis for the service and wildrydes from Kinesis Stream.

 4. Set the Batch size set to 10 and Starting position set to Latest. This small batch size will help us monitor the AWS Lambda error handling clearly from Cloudwatch logs

 5. Set the Batch window to 15. This window will help you batch the incoming messages by waiting for 15 seconds. By default, AWS Lambda will poll messages from Amazon Kinesis Data Stream every 1 sec.

 6. Open the Additional settings section.

 7. Under On-failure destination add the ARN of the wildrydes-queue SQS queue.

 8. Change Retry attempts to 2 and Maximum age of record to 60.

![](https://cdn-images-1.medium.com/max/2000/0*qRN-qiiEk24CKJCo.png)

 1. Leave the rest of the fields to default values.

 2. Click Add to create the trigger.

 3. Click the refresh button until creation is complete and the function shows as Enabled. (You may need to hit the refresh button to refresh the status)

![](https://cdn-images-1.medium.com/max/3410/0*7MpUqvOMgDGulRaY.png)

 1. Return to AWS Cloud9 environment and Insert data into Kinesis Data Stream by running producer binary.

* ./producer -stream wildrydes -error yes -msgs 9

 1. Return to the AWS Lambda function console. Click on the Monitor tab and explore the metrics available to monitor the function.

 2. Click on View logs in CloudWatch to explore the logs in CloudWatch for the log group /aws/lambda/WildRydesStreamProcessor

 3. In the logs you can observe that, there will be error and the same batch will be retried twice ( as we configured retry-attempts to 2)

![](https://cdn-images-1.medium.com/max/4000/0*yYXTFx7kbFiD8YcR.png)

 1. Since the entire batch failed, you should not notice any new records in the DynamoDB table UnicornSensorData. You will see only the 20 records that are inserted from the previous section.

 2. Optionally you can Monitor SQS Queue by following the following steps.

 3. Go to the AWS Management Console, choose Services then search for Simple Queue Service and select the Simple Queue Service.

 4. There will be a message in the wildrydes-queue. This is the discarded batch that had one permanent error in the batch.

 5. Click wildrydes-queue.

 6. Click Send and recieve messages on the top right corner

 7. Click Poll for messages on the bottom right corner

 8. You’ll observe one message. Click the message ID and choose the Body tab. You can see all the details of the discarded batch. Notice that entire batch of messages(Size:9) is discarded even through there was only one error message.

 9. Check the checkbox beside the message ID

 10. Click Delete button. This will delete the message from the SQS queue. This step is optional and is needed only to keep the SQS queue empty.

### 2. Error Handling with Bisect On Batch settings

The retry setting we had before discards entire batch of records even if there is one bad record in the batch. Bisect On Batch error handling feature of AWS Lambda splits the batch into two and retries the half-batches separately. The process continues recursively until there is a single item in a batch or messages are processed successfully.

 1. There are no code changes to the WildRydesStreamProcessor Lambda function. The only change is around setting Kinesis Data Stream configuration. Follow the below steps to remove and add a new Kinesis Data Stream mapping.

 2. Remove the existing Kinesis Data Stream mapping by clicking the Configuration Tab above the code editor. (This step is needed only if there is an existing Kinesis Data Stream mapping or any other Event Source Mapping present for the Lambda function). In the Configuration Tab select the Kinesis:wildrydes (Enabled) and Delete the trigger.

![](https://cdn-images-1.medium.com/max/3414/0*N4QEJut1BfQj8NJ8.png)

 1. Add a new Kinesis Data Stream mapping by clicking the Configuration Tab.

 2. Select the Triggers section and Add trigger button.

 3. Select Kinesis for the service and wildrydes from Kinesis Stream.

 4. Set the Batch size set to 10 and Starting position set to Latest. This small batch size will help us monitor the AWS Lambda error handling clearly from Cloudwatch logs

 5. Set the Batch window to 15. Again, this window will help you batch the incoming messages by waiting for 15 seconds.

 6. Open the Additional settings section.

 7. Under On-failure destination add the ARN of the wildrydes-queue SQS queue.

 8. Change Retry attempts to 2 and Maximum age of record to 60.

 9. Check the box Split batch on error.

![](https://cdn-images-1.medium.com/max/2000/0*T7B-BVbOkpUTo6h0.png)

 1. Leave the rest of the fields to default values.

 2. Click Add to create the trigger.

 3. Click the refresh button until creation is complete and the function shows as Enabled. (You may need to hit the refresh button to refresh the status)

![](https://cdn-images-1.medium.com/max/3410/0*joet9mCUG4T4M-v4.png)

 1. Return to AWS Cloud9 environment and Insert data into Kinesis Data Stream by running producer binary.

    ./producer -stream wildrydes -error yes -msgs 9

 1. Return to the AWS Lambda function console. Click on the Monitor tab and explore the metrics available to monitor the function.

 2. Click on View logs in CloudWatch to explore the logs in CloudWatch for the log group /aws/lambda/WildRydesStreamProcessor

 3. In the logs you can observe that, there will be error and the same batch will be split into two halves and processed. This splitting continues recursively until there is a single item or messages are processed successfully.

![](https://cdn-images-1.medium.com/max/4000/0*4aqAoTtVN1jKkpIZ.png)

 1. Since Bisect-On-Batch splits the batch and processes records,you should notice new records in the DynamoDB table UnicornSensorData. There should be a total of 28 items in UnicornSensorData ( 1 record is an error record ).

 2. Optionally you can Monitor SQS Queue by following the below steps.

 3. Go to the AWS Management Console, choose Services then search for Simple Queue Service and select the Simple Queue Service.

 4. There will be a message in the wildrydes-queue. This is the discarded batch that had one permanent error in the batch.

 5. Click wildrydes-queue.

 6. Click Send and recieve messages on the top right corner

 7. Click Poll for messages on the bottom right corner

 8. You’ll observe one message. Click the message ID and choose the Body tab. You can see all the details of the discarded batch. Notice that this time only one message is discarded.

 9. Check the checkbox beside the message ID

 10. Click Delete button. This will delete the message from the SQS queue. This step is optional and is needed only to keep the SQS queue empty.

## Analytics with Tumbling Windows

In this module, you’ll use the tumbling window feature of AWS Lambda to aggregate sensor data from a unicorn in the fleet in real-time. The Lambda function will read from the Amazon Kinesis stream, calculate the total distance traveled per minute for a specific unicorn, and store the results in an Amazon DynamoDB table.

Tumbling windows are distinct time windows that open and close at regular intervals. By default, Lambda invocations are stateless — you cannot use them for processing data across multiple continuous invocations without an external database. However, with tumbling windows, you can maintain your state across invocations. This state contains the aggregate result of the messages previously processed for the current window. Your state can be a maximum of 1 MB per shard. If it exceeds that size, Lambda terminates the window early. Each record of a stream belongs to a specific window. A record is processed only once, when Lambda processes the window that the record belongs to. In each window, you can perform calculations, such as a sum or average, at the partition key level within a shard.

Resources

 1. [Create a DynamoDB table](https://data-processing.serverlessworkshops.io/stream-processing/04-analytics-with-tumbling-window.html#create_dynamodb_table)

 2. [Create an IAM Role](https://data-processing.serverlessworkshops.io/stream-processing/04-analytics-with-tumbling-window.html#create_iam_role)

 3. [Create a Lambda function](https://data-processing.serverlessworkshops.io/stream-processing/04-analytics-with-tumbling-window.html#create_lambda)

 4. [Monitor the Lambda function](https://data-processing.serverlessworkshops.io/stream-processing/04-analytics-with-tumbling-window.html#monitor_lambda)

 5. [Query the DynamoDB table](https://data-processing.serverlessworkshops.io/stream-processing/04-analytics-with-tumbling-window.html#query_dynamodb_table)

## Implementation

### 1. Create a DynamoDB table

Use the [Amazon DynamoDB](https://console.aws.amazon.com/dynamodbv2/home) console to create a new DynamoDB table. Call your table UnicornAggregation and give it a Partition key called name of type String and a Sort key called windowStart of type String. Use the defaults for all other settings.

✅ Step-by-step Instructions

 1. Go to the AWS Management Console, choose Services then select DynamoDB under Database.

 2. Click Create table.

 3. Enter UnicornAggregation for the Table name.

 4. Enter name for the Partition key and select String for the key type.

 5. Enter windowStart for the Sort key and select String for the key type.

 6. Leave the Default settings box checked and choose Create table.

![](https://cdn-images-1.medium.com/max/2000/0*-EgFgXgThojQJoxQ.png)

### 2. Create an IAM Role for the Lambda function

Use the [IAM](https://console.aws.amazon.com/iamv2/home) console to create a new role. Name it unicorn-aggregation-role and select Lambda for the role type. Attach the managed policy called AWSLambdaKinesisExecutionRole to this role in order to grant permissions for your function to read from Amazon Kinesis streams and to log to Amazon CloudWatch Logs. Create a policy that allows dynamodb:PutItem access to the DynamoDB table created in the last section and attach it to the new role.

✅ Step-by-step Instructions

 1. From the AWS Console, click on Services and then select IAM in the Security, Identity & Compliance section.

 2. Select Policies from the left navigation and then click Create Policy.

 3. Using the Visual editor, we’re going to create an IAM policy to allow our Lambda function access to the DynamoDB table created in the last section. To begin, click Service, begin typing DynamoDB in Find a service, and click DynamoDB.

 4. Type PutItem in Filter actions, and tick the PutItem checkbox.

 5. Click Resources, click Add ARN in table, and construct the ARN of the DynamoDB table you created in the previous section by specifying the Region, Account, and Table Name.

* In **Region**, enter the AWS Region in which you created the DynamoDB table in the previous section, e.g.: us-east-1. In **Account**, enter your AWS Account ID which is a twelve digit number, e.g.: 123456789012. To find your AWS account ID number in the AWS Management Console, click on **Support** in the navigation bar in the upper-right, and then click **Support Center**. Your currently signed in account ID appears in the upper-right corner below the Support menu. In **Table Name**, enter `UnicornAggregation`. You should see your ARN in the **Specify ARN for table** field and it should look similar to:

![](https://cdn-images-1.medium.com/max/2000/0*V93xkOo_KvEZf6wP.png)

 1. Click Add.

![](https://cdn-images-1.medium.com/max/2414/0*enBikImF_qOtXFga.png)

 1. Click Next: Tags.

 2. Click Next: Review.

 3. Enter unicorn-aggregation-ddb-write-policy in the Name field.

 4. Click Create policy.

 5. Select Roles from the left navigation and then click Create role.

 6. Click Lambda for the role type from the AWS service section.

 7. Click Next: Permissions.

 8. Begin typing AWSLambdaKinesisExecutionRole in the Filter text box and check the box next to that role.

 9. Begin typing unicorn-aggregation-ddb-write-policy in the Filter text box and check the box next to that role.

 10. Click Next.

 11. Enter unicorn-aggregation-role for the Role name.

 12. Click Create role.

 13. Begin typing unicorn-aggregation-role in the Search text box.

![](https://cdn-images-1.medium.com/max/2570/0*BTT0xWX_0SNFIyLy.png)

 1. Click on unicorn-aggregation-role and it should look similar to:

![](https://cdn-images-1.medium.com/max/2652/0*rL-b10mc1M_AQIWy.png)

### 3. Create a Lambda function

Use the Lambda console to create a Lambda function called WildRydesAggregator that will be triggered whenever a new record is available in the wildrydes stream. Use the provided index.js implementation for your function code. Create an environment variable with the key TABLE_NAME and the value UnicornAggregation. Configure the function to use the unicorn-aggregation-role role created in the previous sections.

 1. Go to the AWS Management Console, choose Services then select Lambda under Compute.

 2. Click the three lines icon to expand the service menu.

 3. Click Functions.

 4. Click Create function.

 5. Enter WildRydesAggregator in the Function name field.

 6. Select Node.js 14.x from Runtime.

 7. Select unicorn-aggregation-role from the Existing role dropdown.

![](https://cdn-images-1.medium.com/max/2000/0*IVRbzSX98_OMVqjT.png)

 1. Click Create function.

 2. Scroll down to the Code source section.

 3. Double click the index.js file to open it in the editor.

 4. Copy and paste the JavaScript code below into the code editor, replacing all of the existing code:

* const AWS = require("aws-sdk"); AWS.config.update({ region: process.env.AWS_REGION }); const docClient = new AWS.DynamoDB.DocumentClient(); const TableName = process.env.TABLE_NAME; function isEmpty(obj) { return Object.keys(obj).length === 0; } exports.handler = async (event) => { // Save aggregation result in the final invocation if (event.isFinalInvokeForWindow) { console.log("Final: ", event); const params = { TableName, Item: { windowStart: event.window.start, windowEnd: event.window.end, distance: Math.round(event.state.distance), shardId: event.shardId, name: event.state.name, }, }; console.log({ params }); await docClient.put(params).promise(); } console.log(JSON.stringify(event, null, 2)); // Create the state object on first invocation or use state passed in let state = event.state; if (isEmpty(state)) { state = { distance: 0, }; } console.log("Existing: ", state); // Process records with custom aggregation logic event.Records.map((record) => { const payload = Buffer.from(record.kinesis.data, "base64").toString( "ascii" ); const item = JSON.parse(payload); let value = item.Distance; console.log("Adding: ", value); state.distance += value; let unicorn = item.Name; console.log("Name: ", unicorn); state.name = unicorn; }); // Return the state for the next invocation console.log("Returning state: ", state); return { state: state }; };

 1. In the Configuration tab, select the Environment variables section.

 2. Click Edit and then Add environment variable.

 3. Enter TABLE_NAME in Key and UnicornAggregation in Value and click Save.

![](https://cdn-images-1.medium.com/max/2000/0*4Qljj9rIAZ4GVDXT.png)

 1. Scroll up and click on Add trigger from the Function overview section.

![](https://cdn-images-1.medium.com/max/2000/0*P_K4HoGnxqq8kbFX.png)

 1. In the Trigger configuration section, select Kinesis.

 2. Under Kinesis stream, select wildrydes.

 3. Leave Batch size set to 100 and Starting position set to Latest.

 4. Open the Additional settings section.

 5. It is a best practice to set the retry attempts and bisect on batch settings when setting up your trigger. Change Retry attempts to 2 and select the checkbox for Split batch on error.

 6. For Tumbling window duration, enter 60. This sets the time interval for your aggregation in seconds.

![](https://cdn-images-1.medium.com/max/2000/0*M5B5ju2euEm7HcXQ.png)

 1. Click Add and the trigger will start creating.

![](https://cdn-images-1.medium.com/max/2114/0*1fvfw1jUNch0ijBA.png)

 1. Click the refresh button until creation is complete and the trigger shows as Enabled.

 2. Go back to the Code tab and Deploy the Lambda function. You will see a confirmation that the changes were deployed.

![](https://cdn-images-1.medium.com/max/2412/0*GHF3O8sMVt5U-9xm.png)

### 4. Monitor the Lambda function

Verify that the trigger is properly executing the Lambda function and inspect the output from the Lambda function.

✅ Step-by-step Instructions

 1. Return to your Cloud9 environment, and run the producer to start emitting sensor data to the stream.

* ./producer

 1. Click on the Monitor tab. Next, click on View logs in CloudWatch to explore the logs in CloudWatch for the log group /aws/lambda/WildRydesAggregator.

 2. Select the most recent Log stream.

![](https://cdn-images-1.medium.com/max/3132/0*QXU1b0nQED5n1SkL.png)

 1. You can use the Filter events bar at the top to quickly search for matching values within your logs. Use the filter bar, or scroll down, to examine the log events showing the Existing: distance state, Adding: a new distance count, and the Returning state: after the Lambda function is invoked.

![](https://cdn-images-1.medium.com/max/2726/0*I7Ict4d2B5i63AA2.png)

 1. Because we set the tumbling window to 60 seconds, every minute the Final: distance state is aggregated and passed to the DynamoDB table. To see the final distance count, use the filter bar to search for "Final:".

 2. After expanding this log, you will see isFinalInvokeForWindow is set to true, along with the state data that will be passed to DynamoDB.

![](https://cdn-images-1.medium.com/max/2000/0*X2m04sr1lGxvB0lq.png)

### 5. Query the DynamoDB table

Using the AWS Management Console, query the DynamoDB table to verify the per-minute distance totals are aggregated for the specified unicorn.

✅ Step-by-step Instructions

 1. Click on Services then select DynamoDB in the Database section.

 2. Click Tables from the left-hand navigation.

 3. Click on UnicornAggregation.

 4. Click on the View Items button on the top right.

 5. Select Run to return the items in the table. Here you should see each per-minute data point for the unicorn for which you’re running a producer. Verify the state information from the CloudWatch log you viewed was successfully passed to the DynamoDB table.

![](https://cdn-images-1.medium.com/max/2350/0*vwAX5truxcLygm-n.png)

## ⭐ Recap

🔑 The tumbling window feature allows a streaming data source to pass state between multiple Lambda invocations. During the window, a state is passed from one invocation to the next, until a final invocation at the end of the window. This allows developers to calculate aggregates in near-real time, and makes it easier to calculate sums, averages, and counts on values across multiple batches of data. This feature provides an alternative way to build analytics in addition to services like Amazon Kinesis Data Analytics.

🔧 In this module, you’ve created a Lambda function that reads from the Kinesis stream of unicorn data, aggregates the distance traveled per-minute, and saves each row to DynamoDB.

## Error Handling with Checkpoint and Bisect On Batch

While Bisect On Batch is helpful in narrowing down to the problematic messages, it can result in processing previously successful messages more than once. With Checkpoint feature you can return the sequence identifier for the failed messages. This provides more precise control over how to choose to continue processing the stream. For example in a batch of 9 messages where the fifth message fails — Lambda process the batch of messages, items 1–9. The fifth message fails and the function returns the failed sequence identifier. The batch is only retried from message 5 to 9

 1. Go to the AWS Management Console, choose Services then select Lambda under Compute. Alternatively, you can use the search bar and type Lambda in the search dialog box.

 2. Figure out the changes to the WildRydesStreamProcessor function. The changes involve storing the kinesis sequence number (kinesis.sequenceNumber) of the error record and returning the sequence number in the catch block

* ```javascript 'use strict'; const AWS = require('aws-sdk'); const dynamoDB = new AWS.DynamoDB.DocumentClient(); const tableName = process.env.TABLE_NAME; const errorString = 'error'; exports.handler = function(event, context, callback) { console.log('Number of Records sent for each invocation of Lambda function = ', event.Records.length) const requestItems = buildRequestItems(event.Records); const requests = buildRequests(requestItems); Promise.all(requests) .then(() => callback(null, `Delivered ${event.Records.length} records`)) .catch(callback); }; function buildRequestItems(records) { let sequenceNumber = 0; try { return records.map((record) => { sequenceNumber = record.kinesis.sequenceNumber; console.log('Processing record with Sequence Number = ', sequenceNumber); const json = Buffer.from(record.kinesis.data, 'base64').toString('ascii'); const item = JSON.parse(json); if(item.InputData.toLowerCase().includes(errorString)) { console.log ('Error record is = ', item); throw new Error('kaboom') } return { PutRequest: { Item: item, }, }; }); }catch (err) { console.log('Returning Failure Sequence Number =', sequenceNumber) return { "batchItemFailures": [ {"itemIdentifier": sequenceNumber} ] } } } function buildRequests(requestItems) { const requests = []; while (requestItems.length > 0) { const request = batchWrite(requestItems.splice(0, 25)); requests.push(request); } return requests; } function batchWrite(requestItems, attempt = 0) { const params = { RequestItems: { [tableName]: requestItems, }, }; let delay = 0; if (attempt > 0) { delay = 50 * Math.pow(2, attempt); } return new Promise(function(resolve, reject) { setTimeout(function() { dynamoDB.batchWrite(params).promise() .then(function(data) { if (data.UnprocessedItems.hasOwnProperty(tableName)) { return batchWrite(data.UnprocessedItems[tableName], attempt + 1); } }) .then(resolve) .catch(reject); }, delay); }); } ```

 1. Do not forget to click Deploy to deploy the changes to the WildRydesStreamProcessor Lambda function.

 2. Do not forget to Remove the existing Kinesis Data Stream mapping by clicking the Configuration Tab above the code editor. (This step is needed only if there is an existing Kinesis Data Stream mapping or any other Event Source Mapping present for the Lambda function). In the Configuration Tab select the Kinesis:wildrydes (Enabled) and Delete the trigger.

 3. Add a new Kinesis Data Stream mapping by clicking the Configuration Tab. The mapping configuration is same except that you can check mark an additional field Report batch item failures.

 4. Test your changes by inserting data into Kinesis Data Stream.

 5. Monitor CloudWatch logs and Query DynamoDB by repeating steps in the sections [Monitor](https://data-processing.serverlessworkshops.io/stream-processing/04-analytics-with-tumbling-window.html#monitor_lambda) and [Query](https://data-processing.serverlessworkshops.io/stream-processing/04-analytics-with-tumbling-window.html#query_dynamodb_table)

## Enhanced Fan Out

Enhanced fan-out enables consumers to receive records from a stream with throughput of up to 2 MB of data per second per shard. This throughput is dedicated, which means that consumers that use enhanced fan-out don’t have to contend with other consumers that are receiving data from the stream. Kinesis Data Streams pushes data records from the stream to consumers that use enhanced fan-out. Therefore, these consumers don’t need to poll for data.

![](https://cdn-images-1.medium.com/max/2000/0*g3TmA9JAtcQMo2av.png)

For standard iterators, Lambda polls each shard in your Kinesis stream for records at a base rate of once per second. When more records are available, Lambda keeps processing batches until the function catches up with the stream. The event source mapping shares read throughput with other consumers of the shard.

To minimize latency and maximize read throughput, create a data stream consumer with enhanced fan-out. Enhanced fan-out consumers get a dedicated connection to each shard that doesn’t impact other applications reading from the stream. Stream consumers use HTTP/2 to reduce latency by pushing records to Lambda over a long-lived connection and by compressing request headers. You can create a stream consumer with the Kinesis RegisterStreamConsumer API.

    aws kinesis register-stream-consumer --consumer-name con1 \
    --stream-arn arn:aws:kinesis:us-east-2:123456789012:stream/lambda-stream

When you configure Event source mapping, use the consumer name created above as the consumer.

You can also try the template from [serverlessland](https://serverlessland.com/patterns/kinesis-lambda-efo)

## Stream Aggregation

## Streaming Aggregation

In this module, you’ll create an Amazon Kinesis Data Analytics application to aggregate sensor data from the unicorn fleet in real-time. The application will read from the Amazon Kinesis stream, calculate the total distance traveled and minimum and maximum health and magic points for each unicorn currently on a Wild Ryde and output these aggregated statistics to an Amazon Kinesis stream every minute. In the first section, you’ll run the application from a Flink Studio notebook. In the second, optional step, you’ll learn how to deploy the application to run outside the notebook.

## Overview

The architecture for this module involves an Amazon Kinesis Data Analytics application, source and destination Amazon Kinesis streams, and the producer and consumer command-line clients.

The Amazon Kinesis Data Analytics application processes data from the source Amazon Kinesis stream that we created in the previous module and aggregates it on a per-minute basis. Each minute, the application will emit data including the total distance traveled in the last minute as well as the minimum and maximum readings from health and magic points for each unicorn in our fleet. These data points will be sent to a destination Amazon Kinesis stream for processing by other components in our system.

During the workshop, we will use the [consumer.go](https://data-processing.serverlessworkshops.io/client/consumer.go) application to consume the resulting stream. To do so, the application leverages the AWS SDK and acts as Kinesis Consumer.

![](https://cdn-images-1.medium.com/max/4000/0*v_flnspUwIaegeyS.jpg)

## Implement the Stream Aggregation

## Implement the Streaming Aggregation

### 1. Create a Kinesis Data Stream for the summarized events

Use the Amazon Kinesis Data Streams console to create a new stream named wildrydes-summary with 1 shard. This stream will serve as destination for our Kinesis Data Analytics application.

A Shard is the base throughput unit of an Amazon Kinesis data stream. One shard provides a capacity of 1MB/sec data input and 2MB/sec data output. One shard can support up to 1000 PUT records per second. You will specify the number of shards needed when you create a data stream. For example, if we create a data stream with four shards then this data stream has a throughput of 4MB/sec data input and 8MB/sec data output, and allows up to 4000 PUT records per second. You can monitor shard-level metrics in Amazon Kinesis Data Streams and add or remove shards from your data stream dynamically as your data throughput changes by resharding the data stream.

✅ Step-by-step Instructions

 1. Go to the AWS Management Console, click Services then select Kinesis under Analytics.

 2. Click Get started if prompted with an introductory screen.

 3. Click Create data stream.

 4. Enter wildrydes-summary into Data stream name, select the Provisioned mode, and enter 1 into Number of open shards, then click Create Kinesis stream.

 5. Within 60 seconds, your Kinesis stream will be ACTIVE and ready to store real-time streaming data.

### 2. Create an Amazon Kinesis Data Analytics application

In this step, we are going to build an Amazon Kinesis Data Analytics application which reads from the wildrydes stream built in the [Real-time Data Streaming module](https://data-processing.serverlessworkshops.io/streaming-data.html) and emits a JSON object with the following attributes for each minute:

NameUnicorn nameStatusTimeROWTIME provided by Amazon Kinesis Data AnalyticsDistanceThe sum of distance traveled by the unicornMinMagicPointsThe minimum data point of the *MagicPoints* attributeMaxMagicPointsThe maximum data point of the *MagicPoints* attributeMinHealthPointsThe minimum data point of the *HealthPoints* attributeMaxHealthPointsThe maximum data point of the *HealthPoints* attribute

To do so, we will use Kinesis Data Analytics to run an [Apache Flink](https://flink.apache.org/) application. To enhance our development experience, we will use Studio notebooks for Kinesis Data Analytics that are powered by [Apache Zeppelin](https://zeppelin.apache.org/).

Kinesis Data Analytics provides the underlying infrastructure for your Apache Flink applications. It handles core capabilities like provisioning compute resources, parallel computation, automatic scaling, and application backups (implemented as checkpoints and snapshots). You can use the high-level Flink programming features (such as operators, functions, sources, and sinks) in the same way that you use them when hosting the Flink infrastructure yourself. You can learn more about Amazon Kinesis Data Analytics for Apache Flink by checking out the corresponding [developer guide](https://docs.aws.amazon.com/kinesisanalytics/latest/java/what-is.html).

✅ Step-by-step directions

 1. In the AWS Management Console, click Services, select the Kinesis service under Analytics

 2. Choose the Analytics Applications tab in sidebar on the left. If you cannot see a sidebar on the left, please click the Hamburger icon (three vertical lines) to open it.

![](https://cdn-images-1.medium.com/max/NaN/1*b31hiO4ynbDLRrXWEFF4aQ.png)

![](https://cdn-images-1.medium.com/max/NaN/1*b31hiO4ynbDLRrXWEFF4aQ.png)

 1. Select the Studio tab

 2. Click the Create Studio Notebook button. Keep the creation method to the default value.

![](https://cdn-images-1.medium.com/max/NaN/1*b31hiO4ynbDLRrXWEFF4aQ.png)

 1. Name the notebook flink-analytics

 2. In the Permissions panel, click the Create button to create a new AWS Glue database. The AWS Glue service console will open in a new browser tab.

![](https://cdn-images-1.medium.com/max/NaN/1*b31hiO4ynbDLRrXWEFF4aQ.png)

 1. In the AWS Glue console, create a new database named default.

 2. Switch back to your tab with the Studio notebook creation process and click Create Studio notebook.

![](https://cdn-images-1.medium.com/max/NaN/1*b31hiO4ynbDLRrXWEFF4aQ.png)

 1. Once the notebook is created, click the Edit IAM permissions button in the Studio notebook details section.

![](https://cdn-images-1.medium.com/max/NaN/1*b31hiO4ynbDLRrXWEFF4aQ.png)

 1. Make sure to select the default database in the AWS Glue database dropdown. Click the Choose source button in the Included sources in IAM policy section.

![](https://cdn-images-1.medium.com/max/NaN/1*b31hiO4ynbDLRrXWEFF4aQ.png)

 1. Click Browse to select the wildrydes Kinesis data stream as a source. Afterwards, click Save changes.

![](https://cdn-images-1.medium.com/max/NaN/1*b31hiO4ynbDLRrXWEFF4aQ.png)

 1. Click Choose destination followed by Browse to select the wildrydes-summary Kinesis data stream as a output. Afterwards, click Save changes.

![](https://cdn-images-1.medium.com/max/NaN/1*b31hiO4ynbDLRrXWEFF4aQ.png)

 1. Click Save changes the second time to update the IAM policy.

 2. Click on IAM Role link to open it in separate tab. We need to add an additional managed policy to the role that would allow us to delete Glue tables. And we will reuse this policy when deploying the notebook as Flink application later.

![](https://cdn-images-1.medium.com/max/NaN/1*b31hiO4ynbDLRrXWEFF4aQ.png)

 1. Click Add permissions, then Attach Policies, and then Create Policy. Use the Visual editor. Choose Glue as Service.

 2. For the Actions, select GetPartitions from the Read subsection and DeleteTable from the Write subsection.

 3. For the Resources, click Add ARN for catalog and enter your region (e.g. eu-west-1)

 4. For the database, click Add ARN, enter your region and specify default for database name

 5. Finally, for the table, click Add ARN, enter your region, specify default as database, and select Any for the Table name.

![](https://cdn-images-1.medium.com/max/NaN/1*b31hiO4ynbDLRrXWEFF4aQ.png)

 1. Click Next: Tags button and then Next: Review. Specify kinesis-analytics-service-flink-analytics-glue as the policy name and click Create Policy button.

 2. Attach the policy you have just created to the notebook IAM role, by selecting it from the list and clicking Attach Policy button.

 3. Switch back to KDA Studio notebook tab and click Run to run the notebook. As soon it is in the Running state (takes a few minutes), click the Open in Apache Zeppelin button.

 4. In the Apache Zeppelin notebook, choose create a new note. Name it flinkagg and insert the following SQL command. Replace the <REGION> placeholder with the actual region (e.g. eu-west-1).

* %flink.ssql(type=update) DROP TABLE IF EXISTS wildrydes; CREATE TABLE wildrydes ( Distance double, HealthPoints INT, Latitude double, Longitude double, MagicPoints INT, Name VARCHAR, StatusTime AS proctime() ) WITH ( 'connector' = 'kinesis', 'stream' = 'wildrydes', 'aws.region' = '<REGION>', 'scan.stream.initpos' = 'LATEST', 'format' = 'json' ); DROP TABLE IF EXISTS wildrydes_summary; CREATE TABLE `wildrydes_summary` ( Name VARCHAR, StatusTime TIMESTAMP, Distance double, MinMagicPoints INT, MaxMagicPoints INT, MinHealthPoints INT, MaxHealthPoints INT ) WITH ( 'connector' = 'kinesis', 'stream' = 'wildrydes-summary', 'aws.region' = '<REGION>', 'scan.stream.initpos' = 'LATEST', 'format' = 'json' ); INSERT INTO `wildrydes_summary` SELECT Name, TUMBLE_START(StatusTime, INTERVAL '1' MINUTE) AS StatusTime, SUM(Distance) AS Distance, MIN(MagicPoints) AS MinMagicPoints, MAX(MagicPoints) AS MaxMagicPoints, MIN(HealthPoints) AS MinHealthPoints, MAX(HealthPoints) AS MaxHealthPoints FROM wildrydes GROUP BY TUMBLE(StatusTime, INTERVAL '1' MINUTE), Name;

 1. Execute the code by clicking the Play button next to the READY statement on the right side of the cell.

 2. In the Cloud9 development environment, run the producer to start emiting sensor data to the stream.

* ./producer

### 3. Read messages from the stream

Use the command line consumer to view messages from the Kinesis stream to see the aggregated data being sent every minute.

✅ Step-by-step directions

 1. Switch to the tab where you have your Cloud9 environment opened.

 2. Run the consumer to start reading sensor data from the stream. It can take up to a minute for the first message to appear, since the Analytics application aggregates the messages in one minute intervals.

* ./consumer -stream wildrydes-summary

 1. The consumer will print the messages being sent by the Kinesis Data Analytics application every minute:

* { "Name": "Shadowfax", "StatusTime": "2018-03-18 03:20:00.000", "Distance": 362, "MinMagicPoints": 170, "MaxMagicPoints": 172, "MinHealthPoints": 146, "MaxHealthPoints": 149 }

### 4. Experiment with the producer

Stop and start the producer while watching the dashboard and the consumer. Start multiple producers with different unicorn names.

✅ Step-by-step directions

 1. Switch to the tab where you have your Cloud9 environment opened.

 2. Stop the producer by pressing Control + C and notice how the consumer stops receiving messages.

 3. Start the producer again and notice the messages resume.

 4. Hit the (+) button and click New Terminal to open a new terminal tab.

 5. Start another instance of the producer in the new tab. Provide a specific unicorn name and notice data points for both unicorns in consumer’s output:

* ./producer -name Bucephalus

 1. Verify you see multiple unicorns in the output:

* { "Name": "Shadowfax", "StatusTime": "2018-03-18 03:20:00.000", "Distance": 362, "MinMagicPoints": 170, "MaxMagicPoints": 172, "MinHealthPoints": 146, "MaxHealthPoints": 149 } { "Name": "Bucephalus", "StatusTime": "2018-03-18 03:20:00.000", "Distance": 1773, "MinMagicPoints": 140, "MaxMagicPoints": 148, "MinHealthPoints": 132, "MaxHealthPoints": 138 }

## ⭐ Recap

🔑 Amazon Kinesis Data Analytics enables you to query streaming data or build entire streaming applications using SQL, so that you can gain actionable insights and respond to your business and customer needs promptly.

🔧 In this module, you’ve created a Kinesis Data Analytics application that reads from the Kinesis stream of unicorn data and emits a summary row each minute.

## Challenges Faced and Solutions

**Challenge 1: Handling High Volumes of Real-Time Data**

* **Solution**: Utilized Kinesis and Lambda to process data in small batches, ensuring efficient handling of high-throughput streams.

**Challenge 2: Ensuring Data Durability and Query Flexibility**

* **Solution**: Stored raw data in S3 for archiving, leveraging Athena for querying, and DynamoDB for structured data storage.

**Challenge 3: Securing Access Across Services**

* **Solution**: Implemented Cognito for secure, role-based access management, enforcing strict access control for users and applications.

## Conclusion
