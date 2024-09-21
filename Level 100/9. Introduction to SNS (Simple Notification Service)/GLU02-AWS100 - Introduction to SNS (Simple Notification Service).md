# GLU02-AWS100 - Introduction to SNS (Simple Notification Service)

## Cloud Service Provider
- Amazon Web Services

## Difficulty
- Level 100 (Introductory)

## Project's Author(s)

- [Edward Allen Mercado](https://twitter.com/edwardmercado_)

## Objectives

### You need to complete the following:

- Create an SNS topic
- Subscribe to that SNS topic with an email address of yours
- Make sure to accept the subscription in the email you receive
- Send a test message through the SNS topic
- Make sure you received the message to your email address

### You need to complete the following:

## What is Simple Notification Service (SNS)?

**Amazon Simple Notification Service (SNS)** is a fully managed messaging service that enables the **publish-subscribe (Pub/Sub)** messaging model. It allows you to send notifications to multiple recipients, called **subscribers**, by publishing a single message to a **topic**. SNS can deliver messages to a variety of endpoints, making it ideal for application alerts, notifications, and real-time updates.

## How do Pub/Sub notifications work?

In the **Pub/Sub model**:
- A **publisher** sends a message to an **SNS topic**.
- The topic acts as a conduit that **fans out** the message to all **subscribers**.
- Subscribers can be various endpoints like emails, mobile devices, or other AWS services. Each subscriber receives a copy of the published message in near real-time.

## What are the different endpoints that SNS can send notifications to?

Amazon SNS supports sending notifications to the following endpoints:
- **Email**: Sends messages via email.
- **SMS**: Sends text messages to mobile devices.
- **HTTP/HTTPS**: Delivers messages to web servers through HTTP or HTTPS.
- **Amazon SQS**: Delivers messages to Amazon Simple Queue Service (SQS) queues for further processing.
- **AWS Lambda**: Triggers AWS Lambda functions to process the message.
- **Mobile Push Notifications**: Sends notifications to mobile devices via platforms like Apple (APNs) or Google (FCM).

## What happens if a message or notification in SNS cannot be delivered?

If SNS cannot deliver a message to a specific endpoint:
- For **HTTP/HTTPS** endpoints: SNS will attempt to resend the message multiple times (with retries), based on a retry policy. If delivery fails after the retries, the message is discarded.
- For **SQS** or **Lambda**: SNS integrates with dead-letter queues (DLQs) where failed messages can be stored for further analysis.
- For **SMS**: If the message fails due to issues like exceeding quota limits, it is discarded without retries.

## What's the difference between Simple Notification Service (SNS) and Simple Queue Service (SQS)?

While both SNS and SQS are AWS messaging services, they serve different purposes:
- **Amazon SNS (Simple Notification Service)**:
  - **Pub/Sub model**: Used for sending notifications or messages to multiple recipients (subscribers) simultaneously.
  - **Real-time delivery**: Messages are delivered to subscribers in real-time (e.g., email, SMS, or Lambda).
  - Ideal for broadcasting messages to many endpoints.

- **Amazon SQS (Simple Queue Service)**:
  - **Queue-based model**: Messages are sent to a queue where they are stored until processed by consumers.
  - **Asynchronous processing**: Consumers retrieve and process messages from the queue at their own pace.
  - Ideal for decoupling components of a distributed system, ensuring reliable message delivery with no real-time requirement.

## Reference

- [AWS SNS Official Documentation](https://docs.aws.amazon.com/sns/latest/dg/welcome.html)
- [Setting Up Amazon SNS Notifications](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/US_SetupSNS.html)
- [Amazon SNS (from AWS) - The Ultimate Guide](https://www.serverless.com/amazon-sns)
- [What is Amazon SES and SNS in AWS?](https://intellipaat.com/blog/what-is-amazon-ses-sns-in-aws/)

## Costs

- Included in the Free Tier

## Estimated time to complete

- 30 minutes

## Output 
![image](https://github.com/user-attachments/assets/39de2950-f685-420b-8925-b8393da70bf1)
