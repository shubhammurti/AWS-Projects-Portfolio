## Build an automated video monitoring system with AWS IoT and AI/ML : AWS Project

## Introduction

Amazon Web Services (AWS) offers a robust platform for developing cloud-based solutions, designed to cater to the growing demand for scalable, secure, and cost-effective technology. With AWS, professionals can build everything from simple applications to complex enterprise systems, leveraging a suite of globally recognized services such as EC2, S3, Lambda, and DynamoDB.

This blog introduces practical scenarios where AWS services can be utilized to solve real-world problems, empowering developers and cloud enthusiasts to sharpen their skills. The focus is on applying concepts effectively to deploy efficient, scalable, and reliable cloud solutions. Whether you’re a beginner exploring cloud computing or an experienced professional advancing your expertise, AWS’s comprehensive ecosystem serves as a foundation for innovation.

## Prerequisites

* **AWS Account**
Ensure you have an active AWS account to access and deploy resources. Proper billing permissions are essential for provisioning services.

* **Cloud Computing Basics**
Familiarity with cloud concepts, including virtualization, networking, and basic AWS services like EC2 and S3, is helpful for a smoother experience.

* **Programming Fundamentals**
Knowledge of programming concepts and languages (e.g., Python, JavaScript) is beneficial for working with AWS services and automation tools.

* **Technical Setup**
Have a stable internet connection and tools like a modern browser, AWS CLI, and a text editor or IDE installed on your system.

* **Cost Awareness**
Understand AWS pricing and usage limits. Utilize the Free Tier where possible to minimize costs while experimenting with services.

## Technical Stack

* **Amazon EC2**
Scalable virtual servers for hosting applications and workloads.

* **AWS Lambda**
Serverless compute service for running code without managing servers.

* **Amazon S3**
Secure and scalable storage for objects like files and backups.

* **Amazon RDS**
Managed relational databases for engines like MySQL and PostgreSQL.

* **Amazon DynamoDB**
Fully managed NoSQL database for high-speed and scalable applications.

* **Amazon VPC**
Isolated cloud network for secure deployment of AWS resources.

* **AWS IAM**
Access management to control permissions for users and resources.

* **AWS KMS**
Encryption key management for secure data storage.

* **Amazon CloudWatch**
Monitoring and observability service for AWS resources and applications.

* **AWS CloudFormation**
Infrastructure automation using code templates.

* **AWS CLI**
Command-line tool to manage AWS services programmatically.

* **AWS Route 53**
Domain Name System (DNS) service for routing traffic to applications.

## Architecture Diagram

The architecture diagram above illustrates a typical AWS-based web application setup

![](https://cdn-images-1.medium.com/max/3424/0*OWlMIlEsPp8wmLJO.png)

## WebRTC Introduction

WebRTC is an open technology specification for enabling real-time communication (RTC) across browsers and mobile applications via simple APIs. It leverages peering techniques for real-time data exchange between connected peers and provides low media streaming latency required for human-to-human interaction. WebRTC specification includes a set of IETF protocols including Interactive Connectivity Establishment (ICE RFC5245), Traversal Using Relay around NAT (TURN RFC5766), and Session Traversal Utilities for NAT (STUN RFC5389) for establishing peer-to-peer connectivity, in addition to protocol specifications for real-time media and data streaming.

## [WebRTC Connection Flow](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/introduction/webrtc#webrtc-connection-flow)

The following diagram illustrates the connection flow as it occurs using Kinesis Video Streams for WebRTC.

![](https://cdn-images-1.medium.com/max/3840/0*7z_zu8xevgc_-pkY.gif)

## Kinesis Video Streams with WebRTC Components

Kinesis Video Streams provides a standards compliant WebRTC implementation as a fully-managed capability. You can use this capability to securely live stream media or perform two-way audio or video interaction between any camera IoT device and WebRTC compliant mobile or web players. As a fully-managed capability, you do not have to build, operate, or scale any WebRTC related cloud infrastructure such as signaling or media relay servers to securely stream media across applications and devices.

Kinesis Video Streams provides managed end-points for WebRTC signaling that allows applications to securely connect with each other for peer-to-peer live media streaming. Next, it includes managed end-points for TURN that enables media relay via the cloud when applications cannot stream peer-to-peer media. It also includes managed end-points for STUN that enables applications to discover their public IP address when they are located behind a NAT or a firewall. Additionally, it provides easy to use SDKs to enable camera IoT devices with WebRTC capabilities. Finally, it provides client SDKs for Android, iOS, and for Web applications to integrate Kinesis Video Streams WebRTC signaling, TURN, and STUN capabilities with any WebRTC compliant mobile or web player.

## Amazon Rekognition — ML Video Analysis

Amazon Rekognition makes it easy to add image and video analysis to your applications. You just have to provide an image or video to the Amazon Rekognition API, and the service can:

* Identify labels (objects, concepts, people, scenes, and activities) and text

* Detect inappropriate content

* Provide highly accurate facial analysis, face comparison, and face search capabilities

## [Working with stored video analysis](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/introduction/rekognition#working-with-stored-video-analysis)

Amazon Rekognition Video is an API that you can use to analyze videos. With Amazon Rekognition Video, you can detect labels, faces, people etc. in videos that are stored in an Amazon Simple Storage Service (Amazon S3) bucket. Previously, scanning videos for objects or people would have taken many hours of error-prone viewing by a human being. Amazon Rekognition Video automates the detection of items and when they occur throughout a video.

## [Amazon Rekognition Video API overview](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/introduction/rekognition#amazon-rekognition-video-api-overview)

Amazon Rekognition Video processes a video that’s stored in an Amazon S3 bucket. The design pattern is an asynchronous set of operations. You start video analysis by calling a Start operation such as [StartLabelDetection ](https://docs.aws.amazon.com/rekognition/latest/APIReference/API_StartLabelDetection.html). The completion status of the request is published to an Amazon Simple Notification Service (Amazon SNS) topic. To get the completion status from the Amazon SNS topic, you can use an Amazon Simple Queue Service (Amazon SQS) queue or an AWS Lambda function. After you have the completion status, you call a Get operation, such as [GetLabelDetection ](https://docs.aws.amazon.com/rekognition/latest/APIReference/API_GetLabelDetection.html), to get the results of the request.

## Amazon OpenSearch Service

Amazon OpenSearch Service makes it easy for you to perform interactive log analytics, real-time application monitoring, website search, and more. OpenSearch is an open source, distributed search and analytics suite derived from Elasticsearch. Amazon OpenSearch Service offers the latest versions of OpenSearch, support for 19 versions of Elasticsearch (1.5 to 7.10 versions), as well as visualization capabilities powered by OpenSearch Dashboards and Kibana (1.5 to 7.10 versions).

## Step-by-Step Implementation

## 1. Getting Started

[Let’s first review the resources that have already been created for you as part of this workshop:](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/getting-started#let's-first-review-the-resources-that-have-already-been-created-for-you-as-part-of-this-workshop:)

 1. Navigate to the [AWS CloudFormation console ](https://us-west-2.console.aws.amazon.com/cloudformation/home?region=us-west-2#/). (you need to be in the **US West (Oregon)** region to be able to view the resources)

 2. Click on the stack with name **iot304-base-stack** and go to the **Outputs** tab.

![](https://cdn-images-1.medium.com/max/4000/0*xTADZSKkOehRap76.png)

 1. The Amazon OpenSearch Service Domain is pre-created in this workshop. This will be used to store the labels related to entities detected in your streaming videos.

 2. Make a note of the Key (*OpenSearchURL*, *OpenSearchARN*) and Value (*search-kvs-workshop-domain-...*, *arn...*). You'll use them in later parts of the workshop.

 3. You can also explore the **Resources** tab. In addition to the OpenSearch Domain, there is an [AWS Cloud9 ](https://aws.amazon.com/pm/cloud9/)instance also created which you’ll use to host the Video Analytics application (front-end) in later half of this workshop.

![](https://cdn-images-1.medium.com/max/3772/0*rV7upcHdTzXxNNgo.png)

## 3. Create Kinesis Video Stream Resources

As described in the ‘[Kinesis Video Streams with WebRTC Components](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/introduction/kvs/)’ section, a signaling channel is required to establish peer-to-peer connection when you want to enable live-streaming of video. And a video stream is a KVS resource that enables you to transport live video data, store it, and make the data available for consumption both in real time and on a batch or ad hoc basis. In this section, you will create a signaling channel and a video stream in KVS, and initiate streaming from your laptop’s camera through Google Chrome browser. You will first create a peer-to-peer stream to see near real-time video, and then you’ll ingest video into a KVS stream and test the media playback via KVS Video Stream console.

Please make sure you are in the **US West (Oregon)** region for all steps.

## [Creating a signaling channel:](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/kvs#creating-a-signaling-channel:)

 1. In the AWS Management Console, open the [Kinesis Video Streams console](https://us-west-2.console.aws.amazon.com/kinesisvideo/home?region=us-west-2#/)

 2. In the left navigation, click **Signaling channels**. And then click **Create signaling channel**.

![](https://cdn-images-1.medium.com/max/4000/0*w64CKRvhs7VywUfU.png)

 1. On the **Create a new signaling channel** page, type the name for the signaling channel. For this workshop you can use StreamChannel. Leave the default **Time-to-live (Ttl)** value as 60 seconds.

![](https://cdn-images-1.medium.com/max/4000/0*x6A_RcFn_qAaVeL7.png)

 1. Click **Create signaling channel**.

 2. Once the signaling channel is created, review the details on the channel’s details page. Make note of the **Signaling channel ARN**.

## [Creating a video stream:](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/kvs#creating-a-video-stream:)

 1. In the left navigation pane, select **Video streams**. Click **Create video stream**.

![](https://cdn-images-1.medium.com/max/4000/0*XGuUly4_IUQphsJp.png)

 1. On the **Create a new video stream** page, type a name for this stream. For this workshop you can use WebRTCStream. Use the default configuration for other parameters.

![](https://cdn-images-1.medium.com/max/3340/0*20GGZFswdH7LPgeu.png)

 1. Click **Create video stream**.

 2. Once the stream is created, review the details on the **Video Streams** page. Make note of the **Video stream ARN**.

## [Stream video peer-to-peer in near real-time:](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/kvs#stream-video-peer-to-peer-in-near-real-time:)

 1. Open the [Kinesis Video Streams WebRTC Test Page ](https://awslabs.github.io/amazon-kinesis-video-streams-webrtc-sdk-js/examples/index.html). You’ll use this page to initiate the video stream from your system. This page has been created for testing purposes using the [Amazon Kinesis Video Streams WebRTC SDK for JavaScript ](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-js).

![](https://cdn-images-1.medium.com/max/4000/0*BctARYU6ZhyAAgO0.png)

 1. Set the **Region**: us-west-2

 2. Set the **Access Key ID**, **Secret Access Key** and **Session Token**.

* If you are **undertaking this outside of an AWS event and using your own AWS account**, then please retrieve your credentials as you normally would, and paste them here.

* If you are **participating in an AWS event and using an AWS-provided account**, please refer to Step 7 of this [section](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/accessing-workshop-studio/) and the Get AWS CLI credentials option. This is located on the bottom-left corner of the Workshop Studio Event Dashboard. Copy and paste the values within the double quotes (as shown for **AWS_ACCESS_KEY_ID** below).

![](https://cdn-images-1.medium.com/max/4000/0*CbpzT2vOSmlRZOGK.png)

 1. Please Note

 2. While **Session Token** is marked as an ‘Optional’ field in the KVS WebRTC Test Page, you must provide it if you’re participating in an AWS event, with an AWS-provided account.

 3. Set the **Channel Name**: StreamChannel

 4. or as described when creating the signaling channel.

 5. Verify that **Send Video** and **Send Audio** options are enabled under **Tracks**. If not checked already then **please make sure you enable both.**

![](https://cdn-images-1.medium.com/max/3480/0*6VjKmncBFlIam3s7.png)

 1. Click on the **Start Master** button located right above the **Logs** section. It may ask you to **Allow Access** for your browser to access your system’s camera and microphone. Please select **Allow** to proceed.

![](https://cdn-images-1.medium.com/max/2298/0*dzRNDqHs_M6RV_Bx.png)

## [Vew the real-time peer-to-peer stream:](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/kvs#view-the-real-time-peer-to-peer-stream:)

 1. In the [Kinesis Video Streams console ](https://us-west-2.console.aws.amazon.com/kinesisvideo/home?region=us-west-2#/), on the left navigation pane, click **Signaling channels**.

 2. Click on the signaling channel you created earlier (StreamChannel if you gave the same name as suggested in steps above).

 3. Expand the **Media playback viewer** option and press the play button.

![](https://cdn-images-1.medium.com/max/2956/0*CcGzJRjIvhJoLvP4.png)

 1. The peer-to-peer video stream should appear within a few seconds. Put this viewer and the KVS WebRTC Test Page side-by-side and confirm that the latency is minimal. Congratulations, you have a real-time peer-to-peer stream!

 2. Return to the KVS WebRTC Test Page and click on Stop Master.

## [Ingest video into the cloud:](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/kvs#ingest-video-into-the-cloud:)

 1. Now you’ll reconfigure the KVS WebRTC Test Page to use the WebRTC ingest feature to store video in a stream, instead of having a peer-to-peer stream.

* Expand **‘WebRTC Ingestion and Storage’** and provide WebRTCStream as the Stream name (or as described when creating the video stream).

* Click on **Update Media Storage Configuration**. *(You can verify if the configuration was updated successfully or not by scrolling down to the Logs section and looking for the success message as shown in screenshot below)*

![](https://cdn-images-1.medium.com/max/4000/0*jvtN5T34fl93uez5.png)

* Scroll back to the **‘WebRTC Ingestion and Storage’** section and enable the **Ingestion and storage peer joins automatically** option by ticking the checkbox

![](https://cdn-images-1.medium.com/max/4000/0*_SXH-pqqVs2xoj3Q.png)

 1. Click on the **Start Master** button located right above the **Logs** section.

## [View the video stored in the stream:](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/kvs#view-the-video-stored-in-the-stream:)

 1. In the [Kinesis Video Streams console ](https://us-west-2.console.aws.amazon.com/kinesisvideo/home?region=us-west-2#/), on the left navigation pane, click **Video streams**.

 2. Click on the video stream created before (WebRTCStream if you gave the same name as suggested in steps above).

 3. Expand the **Media playback** option.

![](https://cdn-images-1.medium.com/max/4000/0*ZG9WkOVx1X3Nlfvx.png)

 1. Wait for a few seconds and you should now be able to see the video stream coming in from your laptop’s camera. *(Ignore the Download SDK pop-up and in case it persists then just refresh the KVS Video Streams Console page once).* Note that since this video is playing back from storage, it has considerable latency. Congratulations, you have successfully played back video that you ingested and stored in a stream!

 2. Return to the KVS WebRTC Test Page and click on Stop Master.

## 4. Provision supporting resources — Lambda, API Gateway & Step Function

You will now create the following resources which will be used further in the workshop (a CloudFormation script is provided in the next step which will be used to create all the resources mentioned below)-

**Resource Identifier in CloudFormationUsage**kvslambdaThis Lambda function would get the KVS video stream and cut them into smaller chunks and store into S3. This would also call the StartLabelDetection API for Rekognition to start asynchronous detection of labels in the stored video.LambdaRoleThis is the IAM role that will enable AWS Lambda to work with Rekognition, Kinesis Video Streams, OpenSearch cluster, SNS and S3.MyCloudFrontDistributionThis is the CloudFront Distribution URL which would serve the media in our front-end application.rekognitionlambdaSNS would trigger this Lambda function to get the detected labels, their confidence scores and timestamp from Rekognition and store them into Amazon OpenSearch Service.RekognitionRoleThis is the IAM role that will enable Amazon Rekognition to conduct stored video analysis.S3BucketVideoThis is an Amazon S3 Bucket that will be used for storing video snippets. The incoming video streams from KVS would be cut into smaller segments and stored into this S3 bucket.searchApiGatewayThis is a REST API within API Gateway to facilitate search option in the final front-end application.searchlambdaThis Lambda function would be invoked when an end user accesses the front-end application and searches for an entity. The search API would trigger this function which in turn would get the entities from OpenSearch.SnsTopicOnce Rekognition completes label detection for a video clip, it will trigger a notification via this SNS topic.KVSStateMachineStep Function to orchestrate the whole workflow.

## [4.1 Create CloudFormation Stack](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/create-cfn#4.1-create-cloudformation-stack)

Follow the steps mentioned below and pass the Parameter values as described carefully-

 1. Click the following link to launch the CloudFormation stack: [Launch CloudFormation stack in us-west-2 (Oregon)](https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/create/review?stackName=iot304-lambda-stack&templateURL=https://ws-assets-prod-iad-r-pdx-f3b3f9f1a7d6a3d0.s3.us-west-2.amazonaws.com/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/iot304-lambda-stack.yaml)

 2. Under the **Parameters** section of the **Specify stack details** page, provide the following values:

* **KVSStreamName**: WebRTCStream. (This is the name of the KVS Video Stream created in [Section 3](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/kvs/) Step 9.)

* **OpenSearchARN**: This is the ARN for the Amazon OpenSearch Service Domain. Paste the value noted in Step 4 of the ‘[Getting Started](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/getting-started/)’ section. For quick access, you can also navigate to the **Output **section of **iot304-base-stack **[here ](https://us-west-2.console.aws.amazon.com/cloudformation/)and get the value.

* **OpenSearchApiUrl**: This is the domain endpoint for the Amazon OpenSearch Service Domain. Paste the value noted in Step 4 of the ‘[Getting Started](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/getting-started/)’ section. For quick access, you can also navigate to the **Output **section of **iot304-base-stack **[here ](https://us-west-2.console.aws.amazon.com/cloudformation/)and get the value.

![](https://cdn-images-1.medium.com/max/4000/0*_K6zW15OGojeBKGG.png)

 1. Click **Next** till you get to the **Review** page (Step 4 in console). Scroll down till the end and check the box for **I acknowledge that AWS CloudFormation might create IAM resources with custom names** and click **Submit**.

![](https://cdn-images-1.medium.com/max/4000/0*fMsvH80BunFnuQ4V.png)

 1. Wait for the stack creation to reach **CREATE_COMPLETE**.

 2. Once stack is provisioned, make a note of the **Amazon API Gateway URL**, **AWS Lambda Role ARN**, **Amazon CloudFront Distribution** and the **AWS Step Function ARN** from the Outputs section. You'll use these in the upcoming sections.

![](https://cdn-images-1.medium.com/max/4000/0*OgWwCLeN4_aouEXC.png)

## [4.2 Mapping the IAM role for Lambda with Amazon OpenSearch Service domain](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/create-cfn#4.2-mapping-the-iam-role-for-lambda-with-amazon-opensearch-service-domain)

For the **searchlambda** function to be able to work with Amazon OpenSearch Service, for searching or analyzing data stored in OpenSearch, you’ll need to map the Lambda IAM role *(LambdaRole)* created in the section above, with the OpenSearch domain.

 1. Navigate to the [Amazon OpenSearch Service Domain console ](https://us-west-2.console.aws.amazon.com/aos/home?region=us-west-2#opensearch/domains).

 2. Click on the Domain Name kvs-workshop-domain.

 3. Search for the OpenSearch Dashboards URL on the top-right corner and click on it. This will open a new tab for the OpenSearch Dashboards.

![](https://cdn-images-1.medium.com/max/4000/0*Qx0sak87RwKxm-P1.png)

 1. You’ll be prompted to enter the login credentials here. Copy and paste the following and click **Log in**-

* Username: admin

* Password: Amazon90!

 1. Keep the tenant selection as **Global** and **Confirm** (if you get a pop-up asking you to add data, select **Explore on my own**).

![](https://cdn-images-1.medium.com/max/4000/0*prdn5mDYxLvNcEBo.png)

 1. Click on the hamburger menu option on the top-left side of the screen and select **Security** under **Management** section in the left navigation pane.

![](https://cdn-images-1.medium.com/max/4000/0*sJ1iitA9Jw0QMIyF.png)

 1. Click on **Roles** and copy-paste all_access in the Search option and hit **return**/**enter**.

![](https://cdn-images-1.medium.com/max/4000/0*dnH-8L49ZevmfNMi.png)

 1. Click on the **all_access** hyperlink and switch to the **Mapped Users** tab on top half of the screen. Click on **Manage Mapping**.

![](https://cdn-images-1.medium.com/max/4000/0*Z9_dZkIpnJXLMOz-.png)

 1. Scroll down to the **Backend roles** section.

![](https://cdn-images-1.medium.com/max/4000/0*n7enHTq1Zv-Rp48k.png)

 1. You need to paste the IAM Role ARN for **LambdaRole** that you copied earlier in Step 6 [here](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/create-cfn#4.1-create-cloudformation-stack). Or, you can also go back to the [CloudFormation Console ](https://us-west-2.console.aws.amazon.com/cloudformation/home?region=us-west-2#/)and select **iot304-lambda-stack** created in the previous section. And navigate to the **Outputs** tab and copy the Value corresponding to the LambdaRole key.

![](https://cdn-images-1.medium.com/max/4000/0*7FOWYawwvN5ywMb0.png)

 1. Go back to the **OpenSearch Dashboards** console and paste this value under the **Backend roles** section.

![](https://cdn-images-1.medium.com/max/4000/0*yuPV19S1o3Yn-79g.png)

 1. Click on **Map**

 2. Once the role has successfully been added you will see an entry named **Backend role** with **LambdaRole’s ARN** mapped to it

![](https://cdn-images-1.medium.com/max/4000/0*Ibm7m_IsY3cJ7glD.png)

## 5. Set up the front-end search application

You’ll now host the Node.js based ‘**Video Analytics App**’ (front-end application) on an AWS Cloud9 IDE instance. AWS Cloud9 is a cloud-based integrated development environment (IDE) that lets you write, run, and debug your code with just a browser.

This instance was pre-created for you as part of the iot304-base-stack as mentioned in Step 5 of [section 2](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/getting-started/). This application would be your interface to search for entities in video streams and verify the occurrences, timestamps and clips based on labels detected. Artifacts for this app already exist [here ](https://github.com/aws-samples/aws-workshop-for-real-time-video-analysis). You just need to clone this to get started.

 1. Navigate to [AWS Cloud9 Console](https://us-west-2.console.aws.amazon.com/cloud9control/home?region=us-west-2#/)

 2. Click on **Open** under **Cloud9 IDE** for the Environment named kvs-workshop-environment

![](https://cdn-images-1.medium.com/max/4000/0*59zdVOo9mxv9Vgx0.png)

 1. You should see the Welcome page load up. The terminal is on the bottom part of the screen. On the left you have the directory options and on top the **+** sign gives you options to start new files, terminals, configurations etc. -

![](https://cdn-images-1.medium.com/max/4000/0*_KWk3ki-KflhSAKw.png)

 1. Head to the terminal and clone the Git repository. To do this, copy and paste the following into Cloud9 terminal

    git clone https://github.com/aws-samples/aws-workshop-for-real-time-video-analysis

![](https://cdn-images-1.medium.com/max/4000/0*4fjyHvXr0FJ0cpFT.png)

 1. Go to the cloned directory **aws-workshop-for-real-time-video-analysis** in your Cloud9 IDE and expand it. Navigate to **resources** > **code** > **frontend** > **src** > config.js file. Double click on that to open it.

![](https://cdn-images-1.medium.com/max/4000/0*Of4ZLJoqRY89dRcO.png)

 1. Take the value of the Amazon CloudFront Distribution URL and Amazon API Gateway URL copied earlier in Step 6 [here](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/create-cfn#4.1-create-cloudformation-stack). Alternatively, you can get them from the **Outputs **section of the **iot304-lambda-stack **in [CloudFormation ](https://us-west-2.console.aws.amazon.com/cloudformation/home?region=us-west-2#/). These would be the values corresponding to **MyCloudFrontDistribution** and **APIGWURL** Keys (refer to the first screenshot, below). Paste the values in the CLOUDFRONT_URL and API_GW_URL parameter in **config.js** (refer to the second screenshot, below). And save the file.

![](https://cdn-images-1.medium.com/max/4000/0*fRUM7ad6PtYz2TwQ.png)

![](https://cdn-images-1.medium.com/max/3928/0*-zo3a90SS2yJdxzR.png)

 1. In the terminal, cd into the frontend folder within the aws-workshop-for-real-time-video-analysis directory by running the following command:

    cd aws-workshop-for-real-time-video-analysis/resources/code/frontend/

 1. From this directory, run the following command in the terminal:

    npm install

![](https://cdn-images-1.medium.com/max/2868/0*ZFzhmxtxua8YMB2g.png)

 1. Now start the application by running the following command in the terminal once the previous step is completed:

    npm run start

 1. After a few seconds the compilation would complete. Post that, click on the **Preview** option on top.

![](https://cdn-images-1.medium.com/max/4000/0*7ocy51n3DT0Fi5nI.png)

 1. Click on **Preview Running Application**. This would open a small window on the bottom-right part of the screen. Click on **Pop Out Into New Window** option.

![](https://cdn-images-1.medium.com/max/4000/0*ImxXHB4ztqDtO3rT.png)

 1. This would open the application in a new tab in your browser.

![](https://cdn-images-1.medium.com/max/4000/0*ySPjZl9RuGyby7pc.png)

## 6. Tying it all together

Refer to the solution components as listed below to verify all the components you have created till now-

![](https://cdn-images-1.medium.com/max/4000/0*tG1cR05F4nkS5SSU.png)

 1. Your laptop camera and the video feed via webRTC is setup via the [Kinesis Video Streams WebRTC Test Page ](https://awslabs.github.io/amazon-kinesis-video-streams-webrtc-sdk-js/examples/index.html).

 2. Kinesis Video Stream successfully streams video via webRTC (as confirmed in [section 3](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/kvs/) step 16).

 3. kvslambda and the S3 bucket to store videos are created.

 4. SNS topic and rekognitionlambda are created.

 5. OpenSearch Domain is created and required IAM role is attached.

 6. The front-end search app, CloudFront distribution to serve media, searchApiGateway and searchlambda are created and setup.

Now the only 2 steps that you have to do are-

* Restart the Master Feed (as done earlier while testing in [section 3](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/kvs/) step 12): Open the **Kinesis Video Streams WebRTC Test Page** and confirm the values as selected in earlier steps. And click on Start Master button.

* Trigger Step Function, created in [section 4.1](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/create-cfn#4.1-create-cloudformation-stack), to orchestrate KVS-Lambda-Rekognition flow. This is the workflow that connects 2nd and 3rd boxes in the diagram above. To do this, go to the **Cloud9 environment **again. Open a new terminal by clicking on the **+** button.

![](https://cdn-images-1.medium.com/max/2792/0*dricCIUGs9oc2-wY.png)

Now update the *<STATE_MACHINE_ARN>* field in the command mentioned below with the value of **Step Function ARN** obtained from [section 4.1](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/create-cfn#4.1-create-cloudformation-stack) **Step 6**. Or, you can also navigate to the [CloudFormation Console ](https://us-west-2.console.aws.amazon.com/cloudformation/home?region=us-west-2#/)and select **iot304-lambda-stack** created in the previous section and navigate to the **Outputs** tab to copy the Value corresponding to **StepFunctionARN** (refer to the image below the code snippet).

    aws stepfunctions start-execution --state-machine-arn <STATE_MACHINE_ARN> --input "{\"doContinue\" : true}"

![](https://cdn-images-1.medium.com/max/4000/0*InPrz2FGJf6rxwdq.png)

And **run** the command.

![](https://cdn-images-1.medium.com/max/3192/0*rwbrCGqS6QLoNPaV.png)

This will now initiate the whole workflow.

## [Verify the orchestration](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/tying-together#verify-the-orchestration)

To verify if the execution has started, you can go to the [Step Functions Console ](https://us-west-2.console.aws.amazon.com/states/home?region=us-west-2#/statemachines).

![](https://cdn-images-1.medium.com/max/4000/0*tQEh26TdB8hb4GFP.png)

Click on the **KVSStateMachine-** and scroll down to the **Executions**. Select the execution that would be in the **Running** Status and scroll to the **Events** section at the bottom.

![](https://cdn-images-1.medium.com/max/4000/0*dCY7ZuG1VS0MS8b8.png)

**TaskSucceeded** would indicate that the invocations have started. After a few seconds you can go back to the Video Analytics front-end application to begin searching for entities.

## 7. Search Away!

Now that you have all the components created and configured, you can take this setup for a spin.

## [Head back to the front-end application](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/summary#head-back-to-the-front-end-application)

* Refer to step 12 of [section 5.12](https://catalog.us-east-1.prod.workshops.aws/workshops/0c7e49a5-b5c4-4f6d-b26b-9b2d8b5cbd2f/en-US/frontend/) where you had launched preview of the application in your browser. Head back to this preview.

![](https://cdn-images-1.medium.com/max/4000/0*zxwPJFAPuGAxd-Yr.png)

* Here you will see the following options-

* **Search Labels**: This is where you type the entities to search for within your video streams. The application would fetch the values and video frames based on the the labels detected from your video stream.

* **Start and End Date**: You can select the time period within which you’d want to search for the detected entities.

* Try searching for something that could have been there in the video stream. If it was detected, you’ll get an option in form of a drop down menu that you can click on.

![](https://cdn-images-1.medium.com/max/4000/0*AM_giHbxSdAGjKrR.png)

* You should see the results in a similar format-

![](https://cdn-images-1.medium.com/max/4000/0*12Npv-d7l__cPwh0.png)

You can search for other entities similarly.

*With this we have concluded the workshop!*

In real-life scenarios, the webRTC stream that we simulated through our browser and system’s camera and microphone could be replaced with any other source that supports webRTC streaming. These could be mobile devices, Raspberry Pi with USB cameras or even CCTV or IP cameras that support WebRTC streaming.

You can also experiment with adding more functionalities such as setting alerts to highlight specific tagged objects once they are detected by Amazon Rekognition Video.

## Refernce Output

![](https://cdn-images-1.medium.com/max/2000/1*AtwhfSONH5phKPUpSDbF7Q.gif)

## 8. Clean Up

If you undertook this workshop yourself, using your own AWS account, you should conclude by deleting resources to avoid incurring unnecessary costs. Please navigate to the [AWS CloudFormation ](https://console.aws.amazon.com/cloudformation/home?region=us-west-2)console and delete the following stacks:

* **iot304-lambda-stack**

* **iot304-base-stack**

## Conclusion

In this project, I built an automated video monitoring system using AWS IoT and AI/ML services. By integrating AWS IoT Core, I connected video devices to the cloud for real-time data streaming.

Leveraging Amazon Rekognition, I implemented AI-driven video analytics to automatically detect objects, faces, and critical events in video feeds. The system used AWS Lambda and CloudWatch to trigger automated responses based on analysis results, creating an efficient and scalable solution for real-time monitoring.

This project demonstrated the potential of combining IoT and AI/ML to enhance video surveillance capabilities, providing practical benefits in security and operational efficiency.
>  **Shubham Murti — Aspiring Cloud Security Engineer | Weekly Cloud Learning !!**

Let’s connect: [Linkdin](http://www.linkedin.com/in/shubham-murti-b6486a1aa), [Twitter](https://x.com/murti_shubham), [Github](https://github.com/shubhammurti)
