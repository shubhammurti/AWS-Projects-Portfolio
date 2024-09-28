# GLU07-AWS200 - Setup a simple state machine with at least 2 steps
## Cloud Service Provider
- Amazon Web Services

## Difficulty
- Level 200 (Intermediate)

## Estimated Time
- 60 minutes 

## Estimated Cost
- This project is included in the free tier. 


## Project's Author(s)

- [Syed Auther](https://twitter.com/syedauther)

## Objectives

### You need to complete the following:
* Create an AWS Lambda to add 2 numbers supplied as input -[ sample code for step 1](./GLU07-AWS200-SF-step1.py?raw=true)  
* Create an AWS Lambda to return the square of a number-  [ sample code for step 2](./GLU07-AWS200-SF-step2.py?raw=true)  
* Create a state machine to connect the above two Lambdas
	* Go to the step  functions console click on create state machine , do not chnage the default settings.
	* Copy [ this ](./GLU07-AWS200-SF-Template.yaml?raw=true) template to paste into Definition but carefully replace Lambda ARNs with the Lambdas created in above steps where necessary in the template. 
* Execute the state machine and verify the output.


# AWS Step Functions and State Machine Guide

## What is a Step Function?

AWS Step Functions is a fully managed service that allows you to coordinate multiple AWS services into serverless workflows. It provides a visual workflow to manage and automate complex processes and enables you to design and execute workflows that integrate various AWS services such as Lambda, SQS, SNS, and more.

## What is a State Machine?

A state machine is a conceptual model used to define the sequence of states and transitions within a workflow. In AWS Step Functions, a state machine represents the overall structure of a workflow. It defines how different states interact and transition based on specific conditions or inputs. Each state in a state machine performs a particular task or operation, and transitions between states determine the flow of execution.

## What is Workflow Configuration and State Management?

- **Workflow Configuration**: This involves defining the sequence and behavior of tasks within a state machine. It includes setting up states, transitions, and the overall flow of execution. Workflow configuration allows you to specify how different components interact, handle errors, and manage the execution path based on conditions or inputs.

- **State Management**: State management refers to the handling of the data and state of each step within a workflow. It involves tracking the progress, storing intermediate results, and managing the flow of data between different states. State management ensures that the state of each component is maintained accurately throughout the execution of the workflow.

## What is [Amazon States Language](https://docs.aws.amazon.com/step-functions/latest/dg/concepts-amazon-states-language.html)?

Amazon States Language (ASL) is a JSON-based language used to define state machines in AWS Step Functions. It provides a way to specify the states, transitions, and actions within a workflow. ASL includes various constructs for defining states, such as `Task`, `Choice`, `Parallel`, and `Fail`. It allows you to define how data is passed between states, how errors are handled, and how different branches of execution are managed.

## What are Tasks?

In AWS Step Functions, a task is a state that represents a single unit of work within a workflow. Tasks can be AWS Lambda functions, activities, or other service integrations. Each task performs a specific operation and can return results or handle errors. Tasks are the building blocks of a state machine and define the core functionality of the workflow.

## How to Visualize the State Machine?

You can visualize the state machine in AWS Step Functions using the following methods:

1. **AWS Management Console**: The AWS Step Functions console provides a visual representation of your state machine. You can view the workflow diagram, including states and transitions, to understand the structure and flow of your state machine.

2. **State Machine Execution History**: During execution, you can view detailed visualizations of the state machine's progress, including which states have been executed, their input and output data, and any errors encountered.

3. **Graphical View**: Use the graphical view in the AWS Management Console to explore the state machine visually. It helps you see how states are connected and how data flows between them.


## References
- [AWS Step Functions- Getting Started](https://aws.amazon.com/step-functions/)
- [FAQs](https://aws.amazon.com/step-functions/faqs/)
- [Features of Step functions](https://aws.amazon.com/step-functions/features/)
- [Tasks in step functions](https://docs.aws.amazon.com/step-functions/latest/dg/amazon-states-language-task-state.html)
- [Wait state in step functions](https://docs.aws.amazon.com/step-functions/latest/dg/amazon-states-language-wait-state.html)
- [I/O data  processing ](https://docs.aws.amazon.com/step-functions/latest/dg/concepts-input-output-filtering.html)

## Ideas
- Just create a Lambda function with default settings and choose the language you want to code in, if you do not want the exact same implementation as this excercise. Make your own flow, take a look at some [use cases](https://aws.amazon.com/step-functions/use-cases/)

## Output
![image](https://github.com/user-attachments/assets/cccc7a40-7061-4ee2-9cb2-5b8087c027e9)
