# DBS03-AWS200 - Create an Aurora RDS Database

## Cloud Service Provider
- Amazon Web Services

## Difficulty
- Level 200 (Intermediate)

## Project's Author(s)
- [Nathan Cho](https://twitter.com/hatchcanon)

## Objectives

### You need to complete the following:
- Create a Security Group in your default VPC that allows traffic from `0.0.0.0/0` (public internet) on port `3306`
- Use the "standard create" mode and choose "MySQL compatibility" with "regional" and "Dev/Test" mode
- Specify your own password for the database
- Choose the db.r5.large instance size
- Choose the region's default VPC
- Enable "Public Access" and add the above created Security Group
- Create the database
- Connect from your computer to the newly created database with a MySQL DBMS like [MySQL Workbench](https://dev.mysql.com/downloads/workbench/?os=src) or [Sequel Ace](https://github.com/Sequel-Ace/Sequel-Ace)
- Create a test table in your database to verify everything is working correctly
- Delete the database

### You need to answer the following:

## What Type of Database is Aurora?

Amazon Aurora is a fully managed relational database engine that is compatible with MySQL and PostgreSQL. It offers high performance, scalability, and availability.

## Minimum Storage for Aurora

Aurora automatically scales storage from 10 GB to 128 TB in 10 GB increments. There is no fixed minimum storage requirement as Aurora scales storage based on the needs of your database.

## Aurora Serverless vs. Regular RDS DB Instances

**Aurora Serverless**:
- Aurora Serverless automatically adjusts the database's compute capacity based on the application's needs, scaling up or down as necessary.
- It is billed based on the actual capacity consumed rather than a fixed instance size.
- Ideal for variable workloads or applications with unpredictable database usage patterns.

**Regular RDS DB Instances**:
- Requires you to choose a specific instance size with a fixed amount of compute and memory.
- You need to manually adjust the instance size based on your application's workload.
- Better suited for predictable workloads with consistent usage patterns.

## Aurora's Data Distribution and Redundancy

Aurora replicates data across multiple Availability Zones (AZs) within an AWS Region. The primary database's data is automatically replicated to up to 5 read replicas in different AZs to ensure high availability and durability. For more redundancy, you can:
- Use Aurora Global Databases to replicate data across multiple AWS Regions.
- Utilize Aurora's built-in failover capabilities to handle AZ failures.

## Aurora's Read & Write Replicas

- **Write Replicas**: The primary instance handles all write operations and can have multiple read replicas for handling read operations.
- **Read Replicas**: Serve read-only queries to offload read traffic from the primary instance and improve performance.

## Reader vs. Writer Endpoints/Instances

- **Writer Endpoint/Instance**: The instance that handles all write operations and maintains the primary database.
- **Reader Endpoint/Instance**: Instances that handle read-only operations, distributing read traffic to improve performance and reduce load on the primary instance.

## Types of Aurora Endpoints

1. **Writer Endpoint**: Routes write queries to the primary instance.
2. **Reader Endpoint**: Routes read queries to one of the available read replicas.
3. **Cluster Endpoint**: Provides a connection to the primary instance and can be used for both reads and writes.
4. **Instance Endpoint**: Provides direct access to a specific instance, either primary or read replica.

## Aurora Database Encryption

Yes, Aurora offers database encryption. You can enable encryption at rest using AWS Key Management Service (KMS) to encrypt your database storage and backups.

## Public Access

**Why is it a Bad Idea to Enable "Public Access"?**
- Enabling public access exposes your database to the internet, increasing the risk of unauthorized access and potential security vulnerabilities.

**Why We Enabled Public Access This Time?**
- In this case, public access was enabled for testing or development purposes to allow easy connectivity from an external source. It is important to ensure proper security measures and remove public access when the database is no longer in use or when moving to production.

## References
- [AWS Create a DB Instance](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_Tutorials.WebServerDB.CreateDBInstance.html)
- [RDS FAQs](https://aws.amazon.com/rds/faqs/)
- [An Introduction to Amazon Aurora](https://dzone.com/articles/an-introduction-of-amazon-aurora)

## Costs
- Amazon Aurora is not included in the free tier
- An Aurora database running on the (cheapest) db.r5.large instance [will cost $0.29 per hour](https://aws.amazon.com/rds/aurora/pricing/)

## Estimated time to complete
- 60 minutes

## Tips
- To delete the database, make sure that you have disabled "deletion protection"

## Outputs
![image](https://github.com/user-attachments/assets/7ffefe8c-92f7-4f9b-a01d-3bfdc3cc2f3a)

