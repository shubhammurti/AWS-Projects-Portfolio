# DBS03-AWS100 - Creating an Amazon RDS DB Instance (MS SQL Server)

## Cloud Service Provider

- Amazon Web Services


## Difficulty

- Level 100 (Introductory)


## Project's Author(s)

- [Jagan](https://twitter.com/JAG2wt)

## Objectives

### You need to complete the following:


- Setup a database instance on Amazon RDS
- Create a MS SQL Server database instance on RDS
- Connect to RDS database instance from your local

### You need to answer the following:

## What is RDS?

Amazon RDS (Relational Database Service) is a managed relational database service provided by AWS. It simplifies the setup, operation, and scaling of relational databases in the cloud. With RDS, you can easily set up and operate a database with high availability and automatic backups, patching, and scaling. It supports several database engines, including:

- Amazon Aurora
- MySQL
- MariaDB
- PostgreSQL
- Oracle
- Microsoft SQL Server

## How to Create a Database Instance on RDS

Follow these steps to create a database instance on Amazon RDS:

1. **Sign in to the AWS Management Console**: Go to [AWS Management Console](https://aws.amazon.com/console/) and sign in with your credentials.

2. **Navigate to RDS**: In the AWS Management Console, search for and select "RDS" to open the RDS dashboard.

3. **Launch a Database Instance**:
    - Click on "Databases" in the left-hand menu.
    - Click on the "Create database" button.
    - Choose a database creation method: "Standard Create" or "Easy Create". For more control, select "Standard Create".

4. **Select a Database Engine**:
    - Choose the database engine you want to use (e.g., MySQL, PostgreSQL).

5. **Specify Database Details**:
    - **DB Instance Class**: Choose the instance type based on your needs.
    - **Storage**: Define the allocated storage and type.
    - **DB Instance Identifier**: Enter a unique name for your database instance.
    - **Master Username and Password**: Provide the credentials for the database master user.

6. **Configure Advanced Settings**:
    - Configure options like VPC, subnet group, security group, backup, maintenance, and monitoring as needed.

7. **Create the Database Instance**:
    - Review your settings and click "Create database" to launch the instance.

## How to Connect to an RDS Database

To connect to your RDS database instance, follow these steps:

1. **Obtain Connection Information**:
    - Go to the RDS dashboard in the AWS Management Console.
    - Click on "Databases" and select your database instance.
    - Note the endpoint and port of your database instance under the "Connectivity & security" tab.

2. **Configure Security Groups**:
    - Ensure that the security group associated with your RDS instance allows inbound traffic on the database port (default ports: 3306 for MySQL, 5432 for PostgreSQL, etc.).
    - Add inbound rules to allow traffic from your IP address or application server.

3. **Connect Using a Database Client**:
    - Use a database client or command-line tool (e.g., MySQL Workbench, pgAdmin, or `psql` for PostgreSQL) to connect.
    - Enter the endpoint, port, master username, and password to establish a connection.

## References
- [What is RDS?](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html)
- [Setting Up for Amazon RDS](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_SettingUp.html)
- [Creating an Amazon RDS DB Instance](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_CreateDBInstance.html)
- [Connecting to a DB Instance Running the Microsoft SQL Server Database Engine](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ConnectToMicrosoftSQLServerInstance.html)
- [Running SQL Server Databases on Amazon RDS for SQL Server - AWS Virtual Workshop](https://youtu.be/twOglkIFbXU)
- [Amazon RDS Free Tier](https://aws.amazon.com/rds/free/)

## Costs

- Included in the Free Tier


## Estimated time to complete
- 45-60 minutes


## Tips
- Having database knowledge is an added advantage
- 750 hours of Amazon RDS Single-AZ `db.t2.micro` included in free tier

## Output
![image](https://github.com/shubhammurti/AWS-Projects-Portfolio/blob/8ab9a8b06657034dd2ac5604f4a926707a535bf6/Level%20100/5.%20Creating%20an%20Amazon%20RDS%20DB%20Instance%20(MS%20SQL%20Server)/RDS.png)

