# DBS05-AWS100 - Create a DynamoDB table

## Cloud Service Provider
- Amazon Web Services

## Difficulty
- Level 100 (Introductory)

## Project's Author(s)
[Chris Nagy](https://twitter.com/chris_the_nagy)

## Objectives

### You need to complete the following:
- Create a DynamoDB table with provisioned capacity
- Create three random items in the table
- Run a scan on the table that returns all three items
- Run a query on the table that returns a single item

### You need to answer the following:

## What is an "item" in DynamoDB?
An **item** in DynamoDB is a single record in a table, which is composed of attributes. Each item is uniquely identified by a primary key and can hold different types of data within its attributes.

## What data types can you store in a DynamoDB table?
DynamoDB supports three primary types of data:
- **Scalar types**: String, Number, Binary, Boolean, and Null.
- **Set types**: String Set, Number Set, and Binary Set.
- **Document types**: List and Map.

## What is the maximum size of an item in DynamoDB?
The maximum size of an item in DynamoDB is **400 KB**, including all attribute names and values.

## What capacity modes are available for DynamoDB?
DynamoDB provides two capacity modes:
1. **On-Demand Mode**: DynamoDB scales automatically based on traffic, charging per read and write request.
2. **Provisioned Mode**: You specify the read and write capacity units (RCU/WCU), and DynamoDB will manage throughput based on the provisioned capacity.

## What are Write Capacity and Read Capacity Units (WCU/RCU)?
- **Write Capacity Unit (WCU)**: One WCU represents one write per second for items up to 1 KB in size.
- **Read Capacity Unit (RCU)**: One RCU represents one strongly consistent read per second for items up to 4 KB in size or two eventually consistent reads per second for items up to 4 KB.

## What is the size of a single WCU and RCU?
- **WCU**: A single WCU can write 1 KB per second.
- **RCU**: A single RCU can read 4 KB per second for strongly consistent reads or 8 KB per second for eventually consistent reads.

## How does DynamoDB support autoscaling?
DynamoDB automatically adjusts provisioned throughput based on traffic patterns when **Auto Scaling** is enabled. It adjusts the read and write capacity units up or down in response to actual traffic to maintain optimal performance and avoid overprovisioning.

## Does DynamoDB support encryption?
Yes, DynamoDB supports encryption at rest using **AWS Key Management Service (KMS)**. You can choose to use AWS-managed keys or your own customer-managed keys for encryption.

## Which key type is required for creating a table?
A **Primary Key** is required when creating a DynamoDB table. It can be a simple primary key (Partition Key) or a composite primary key (Partition Key + Sort Key).

## Which three data types does the Primary Key support?
The Primary Key in DynamoDB supports three scalar data types:
1. **String**
2. **Number**
3. **Binary**

## What is the difference between a Primary (Hash) Key and a Secondary (Sort) Key?
- **Primary Key (Hash Key)**: This uniquely identifies an item in a DynamoDB table. It is used to distribute data across partitions.
- **Secondary Key (Sort Key)**: Used along with the primary key in a composite key to enable efficient queries by specifying additional filtering criteria.

## What is a DynamoDB Stream?
A **DynamoDB Stream** captures a time-ordered sequence of changes made to items in a table. You can use streams to track insert, update, and delete operations and trigger AWS Lambda functions or other integrations based on those changes.

## What are Global Tables?
**Global Tables** provide a fully replicated, multi-region solution for DynamoDB tables. This allows for automatic data replication across multiple AWS Regions, providing high availability and low-latency access to data from any location.

## How do backups work in DynamoDB?
DynamoDB supports **on-demand backups** and **continuous backups** (using **Point-in-Time Recovery**). On-demand backups are user-initiated and allow you to create full backups of tables at any point. Point-in-Time Recovery enables you to restore your table to any second in time from the past 35 days.

## Can DynamoDB be performant at-scale?
Yes, DynamoDB can scale horizontally to handle millions of requests per second with consistent low-latency performance. It is highly scalable, both in terms of throughput and storage, making it an ideal choice for applications with unpredictable or high-scale workloads.



## References
- [AWS Create and Query a NoSQL Table](https://aws.amazon.com/getting-started/hands-on/create-nosql-table/)
- [DynamoDB FAQs](https://aws.amazon.com/dynamodb/faqs/)

## Costs
- 25GB of storage is included in the free tier
- 25 WCUs/RCUs are included in the free tier

## Estimated time to complete
- 30 minutes

## Tips
- Use numbers as your Primary Keys for this getting started project.
- Do not use a sort key for this project.

## OupPut
![image](https://github.com/user-attachments/assets/f967a9a8-4c6e-4269-becf-cdeec1119200)
