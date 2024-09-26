# COM04-AWS200 - Deploy a Docker container image on AWS Fargate

## Cloud Service Provider

- Amazon Web Services

## Difficulty

- Level 200 (Intermediate)

## Project's Author(s)

- [Johan Rin](https://twitter.com/johanrin)

## Objectives

### Prerequisites

- [Push a Docker image to Amazon ECR repository](https://github.com/shubhammurti/AWS-Projects-Portfolio-pvt/blob/4b08582137ffc44b01226fb4fdaf22d829fffcbc/LEVEL100/4.%20Push%20a%20Docker%20image%20to%20Amazon%20ECR%20repository/COM04-AWS100%20-%20Push%20a%20Docker%20image%20to%20Amazon%20ECR%20repository.md)

### You need to complete the following:

- Configure your container with your Docker image
- Configure your task definition
- Define your service
- Configure your cluster

### You need to answer the following:

## What is a _container_?
A container is a lightweight, standalone, and executable software package that includes everything needed to run an application: code, runtime, libraries, and system tools. Containers allow applications to run consistently across various computing environments by encapsulating them and their dependencies.

## What is the difference between Soft memory limit and Hard memory limit for a custom container?
- **Hard Memory Limit**: This is the maximum amount of memory a container can use. If the container exceeds this limit, it will be terminated by the system.
- **Soft Memory Limit**: This is a preferred amount of memory that the container would like to use. The container can exceed this limit if there is available memory on the host, but it is not guaranteed.

## What is a _task definition_?
A task definition is a blueprint used by Amazon ECS to run containers. It specifies the container image to use, the required resources (CPU and memory), networking configurations, and other settings like environment variables. It essentially defines how a container should be run.

## What is the name of the default task execution role?
The default task execution role is named `ecsTaskExecutionRole`. This role is required for tasks to pull container images from Amazon ECR and to send logs to Amazon CloudWatch Logs.

## What does a task size allow?
Task size allows you to define the CPU and memory resources allocated to a task. It ensures that the container has the necessary resources to operate efficiently and helps manage resource allocation within the ECS cluster.

## What is a _service_?
A service in Amazon ECS is responsible for running and maintaining a specified number of task instances simultaneously. It ensures that the desired number of tasks are running and can be configured to automatically replace tasks if they stop or fail.

## Which load balancer type Fargate can handle?
Fargate can handle two types of load balancers:
- **Application Load Balancer (ALB)**: Operates at the application layer (Layer 7) and provides features like content-based routing.
- **Network Load Balancer (NLB)**: Operates at the transport layer (Layer 4) and handles high-throughput and low-latency requirements.

## How many security groups are created by default if you use a load balancer?
By default, if you use a load balancer with Amazon ECS, two security groups are created: one for the load balancer and one for the ECS tasks.

## What is a _cluster_?
A cluster in Amazon ECS is a logical grouping of container instances or Fargate tasks that you can manage and deploy services to. It allows you to organize and manage multiple tasks and services efficiently.

## What are cluster names limitations?
Cluster names in Amazon ECS have the following limitations:
- They must be unique within an AWS account and region.
- They can be up to 255 characters long.
- They can contain uppercase and lowercase letters, numbers, hyphens, and underscores.



## References

- [Getting started with Amazon ECS using Fargate](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/getting-started-fargate.html)
- [Deploy Docker Containers](https://aws.amazon.com/getting-started/hands-on/deploy-docker-containers/)
- [How Amazon ECS manages CPU and memory resources](https://aws.amazon.com/blogs/containers/how-amazon-ecs-manages-cpu-and-memory-resources/)
- [Amazon ECS Task Execution IAM Role](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_execution_IAM_role.html)

## Costs

- Included in the Free Tier

## Estimated time to complete

- 45 minutes - only if you already have a Docker image

## Output
![{EE0846AB-2E76-4374-BE58-6CE15E4501D2}](https://github.com/user-attachments/assets/0fb34872-8def-4485-a704-a863cdff2263)

