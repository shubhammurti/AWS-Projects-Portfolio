##  Deploying a Complete Machine Learning Fraud Detection Solution Using Amazon SageMaker : AWS Project

### Introduction

This project leverages Amazon SageMaker and key AWS services to build a scalable, real-time fraud detection solution. By utilizing Amazon SageMaker’s machine learning capabilities, combined with services such as AWS Lambda, S3, and API Gateway, this setup processes transaction data to identify fraudulent patterns efficiently. It provides a robust framework for secure, automated, and reliable fraud detection, designed for seamless integration into production environments where real-time insights are essential.

### Tech Stack

This solution leverages a range of AWS services, each playing a crucial role in creating a scalable, secure, and responsive machine learning infrastructure:

* **Amazon SageMaker**: Core platform for model training, deployment, and hosting.

* **AWS Lambda**: Automates resource creation, orchestrates SageMaker integrations, and handles infrastructure setup.

* **Amazon S3**: Stores training data, model artifacts, and log files.

* **AWS IAM**: Manages access control with defined roles and policies.

* **Amazon EC2 and VPC**: Provides network isolation and backend processing capabilities.

* **Amazon CloudWatch**: Enables monitoring and alerting for various system components.

* **Amazon SQS**: Manages asynchronous task queues for inter-service communication.

**Additional Services**:

* **AWS Secrets Manager**: Safeguards sensitive information such as API keys.

* **AWS CloudTrail**: Tracks account activity and resource changes.

* **Amazon Route 53**: Manages domain name resolution for the API endpoint.

* **AWS Systems Manager (SSM)**: Provides parameter management and infrastructure automation.

* **Amazon API Gateway**: Exposes model predictions as RESTful APIs.

* **Amazon SNS**: Sends alerts and notifications based on specific events.

* **Amazon CloudFormation**: Automates infrastructure provisioning.

### Prerequisites

Before beginning, ensure you have:

 1. **Basic AWS Knowledge**: Familiarity with Amazon SageMaker, IAM, Lambda, and S3.

 2. **Python and ML Basics**: Knowledge of Python for model training and AWS SDK integration.

 3. **AWS CLI and SDKs**: Installed and configured for seamless AWS service management.

 4. **IAM Permissions**: Appropriate permissions to interact with SageMaker, S3, Lambda, and other services used in the project.

### Problem Statement or Use Case

Detecting fraudulent transactions is a challenge for financial institutions due to the high volume and complexity of real-time data. Fraud detection models need to be scalable, secure, and capable of integrating seamlessly with backend systems to process transactions in real-time. This project addresses these needs by developing a machine learning-based fraud detection model that:

* **Learns and Identifies Fraud Patterns**: Uses machine learning to analyze transaction data and classify transactions as legitimate or suspicious.

* **Ensures Scalability and Efficiency**: Deploys a highly scalable, serverless architecture using SageMaker and Lambda.

* **Enables Real-Time Monitoring and Notifications**: Implements CloudWatch, CloudTrail, and SNS for tracking and alerting on model performance and anomalies.

The solution is ideal for large-scale fraud detection in production environments, enabling real-time insights with minimal manual intervention.

## Architecture Diagram

The architecture diagram below shows the interaction between various AWS services, highlighting the flow of data from transaction storage to model inference and result distribution.

![](https://cdn-images-1.medium.com/max/2224/1*AEoYpzMMEG8M16rdnh7OtA.png)

## Step-by-Step Implementation

## Launch the CloudFormation Stack

## [Local Computer](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/20-environmentsetup/22-selfpaced/cloudformation#local-computer)

Download the CloudFormation template to your local computer:

    curl 'https://static.us-east-1.prod.workshops.aws/public/aed5dc57-f15e-4afa-bbf4-9ff167491648/static/fraud-detection-workshop-selfpaced.yaml' --output fraud-detection-workshop-selfpaced.yaml

## [Within your AWS account](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/20-environmentsetup/22-selfpaced/cloudformation#within-your-aws-account)

 1. Navigate to [AWS CloudFormation ](https://console.aws.amazon.com/cloudformation/home#/stacks/create/template)(AWS Console) to create a new stack.

 2. On **Create stack** screen, under the **Specify a template** section, select **Upload a template file** option and navigate to select fraud-detection-workshop-selfpaced.yml file you downloaded earlier. Click **Next**.

![](https://cdn-images-1.medium.com/max/2526/0*EBwt0WucGmGkO_Bj.png)

 1. On **Specify stack details** screen, under the **Stack name** section, provide a name for the CloudFormation stack such as fraud-detection-workshop.

 2. Leave the rest of the parameters unchanged, and click **Next**

![](https://cdn-images-1.medium.com/max/2000/0*_119NbBqQfc3DtUp.png)

 1. On the **Configure stack options** screen, leave default parameters unchanged, scroll to the bottom of the page, and click **Next**

 2. On the **Review fraud-detection-workshop** screen, scroll to the bottom of the page and check off the box “I acknowledge that AWS CloudFormation might create IAM resources.”. Click **Create Stack**.

![](https://cdn-images-1.medium.com/max/2076/0*UG6pF6yxRmFHtgIx.png)

STOP: Cloudformation will take a few minutes to run and set up your environment. Please wait for this step to finish.

**Congratulations!** You have successfully deployed AWS environment for this workshop. Next, we will verify this environment.

Click “Next” to go to the next section.

## Overview of the Environment

In this section, we’re going to go through a quick overview of the workshop and check if everything is set up correctly.

* [Workshop Overview](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/20-environmentsetup/23-overviewoftheenvironment#workshop-overview)

* [Verify SageMaker Studio is ready](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/20-environmentsetup/23-overviewoftheenvironment#verify-sagemaker-studio-is-ready)

* [Explanation of the code files](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/20-environmentsetup/23-overviewoftheenvironment#explanation-of-the-code-files)

* [Explanation of the data files](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/20-environmentsetup/23-overviewoftheenvironment#explanation-of-the-data-files)

* [Explanation of helper scripts](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/20-environmentsetup/23-overviewoftheenvironment#explanation-of-helper-scripts)

## [Workshop Overview](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/20-environmentsetup/23-overviewoftheenvironment#workshop-overview)

In this workshop we will -

* **Explore, clean, visualize and prepare the data**: This step is all about understanding the auto insurance claims data.

* **Select & engineer features**: Here we will get acquainted with Amazon SageMaker Feature Store.

* **Build and train a model**: Train your model through the SageMaker API.

* **Deployment & Inference**: Learn to deploy your model through quick commands for Real-time inference.

* **(Bonus) Transform data visually**: Learn to transform and visualize data through Amazon SageMaker DataWrangler.

* **(Bonus) Detect bias in the dataset**: Learn to use Amazon SageMaker Clarify to detect bias in a bonus lab.

* **(Bonus) Batch transforms**: Learn to batch inference requests and use SageMaker Batch Transforms.

* **Finally**, put everything together into a production CI/CD pipeline using Amazon SageMaker Pipelines

We are going to make use of three core jupyter notebooks.

 1. The first notebook (Lab_1_and_2-Data-Exploration-and-Features.ipynb) demonstrates Exploratory Data Analysis (EDA). Specifically, data visualization, manipulation and transformation through Pandas and Seaborn python libraries. It will then walk you through feature engineering and getting the data ready for training.

 2. The second notebook (Lab_3_and_4-Training_and_Deployment.ipynb) demonstrates training and deployment of the model followed by validation of the predictions using a subset of the data. Once deployed, the next step shows how to get predictions from the model.

 3. The third notebook (Lab_5-Pipelines.ipynb) showcases a pipeline which integrates all previous steps. This is a good example on how to operationalize a Machine Learning Model into a production pipeline. This is a stand-alone lab which doesn't require executing the first two notebooks.

## [Verify SageMaker Studio is ready](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/20-environmentsetup/23-overviewoftheenvironment#verify-sagemaker-studio-is-ready)

 1. Navigate to [AWS console ](https://console.aws.amazon.com/)browser window and type SageMaker in the search bar at the top of the AWS console home page. Click on [Amazon SageMaker ](https://console.aws.amazon.com/sagemaker/home)service page in the AWS console.

 2. Click on the Studio link in the left navigation pane under Control Panel.

![](https://cdn-images-1.medium.com/max/2000/0*oRy8UUylVLhYMTwy.png)

 1. Next, you should see a user is already setup for you. Click on “Open Studio”.

![](https://cdn-images-1.medium.com/max/2000/0*xU_bfN-PFpgQNoyI.png)

 1. This will open SageMaker Studio UI in new browser window.

Attention

Amazon SageMaker Studio and Amazon SageMaker Studio Classic are two of the machine learning environments that you can use to interact with SageMaker. In this workshop, we will use SageMaker Studio Classic experience.

The Amazon SageMaker Studio UI extends the SageMaker Studio Classic interface. Click on “Studio Classic” icon under Applications.

![](https://cdn-images-1.medium.com/max/4000/0*JBDMJL0p1nwK4JDw.png)

The Amazon SageMaker Studio Classic interface is based on JupyterLab, which is a web-based interactive development environment for notebooks, code, and data. Keep this window open.

![](https://cdn-images-1.medium.com/max/4000/0*QGMWUASR40Tj1__x.png)

Now let’s walk through the various files and resources pre-provisioned for you.

## [Explanation of the code files](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/20-environmentsetup/23-overviewoftheenvironment#explanation-of-the-code-files)

There are five notebooks in the folder FraudDetectionWorkshop:

![](https://cdn-images-1.medium.com/max/2000/1*MXrxD4T93w-WQv3oPiVjuA.png)

## [Explanation of the data files](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/20-environmentsetup/23-overviewoftheenvironment#explanation-of-the-data-files)

The target data exists in the data directory. Below is a list of files and their brief description.

![](https://cdn-images-1.medium.com/max/2000/1*CQ9Y77wXVs1ITxovTwBUcw.png)

## [Explanation of output files](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/20-environmentsetup/23-overviewoftheenvironment#explanation-of-output-files)

The outputs directory contains two files that contain data transformations. We will use these files in Lab 5.

* claims_flow_template

* customer_flow_template

## [Explanation of helper scripts](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/20-environmentsetup/23-overviewoftheenvironment#explanation-of-helper-scripts)

There are seven helper scripts in scripts directory:

![](https://cdn-images-1.medium.com/max/2000/1*zQmSI6TcmgDJk6A-IKYNvA.png)

Attention

If for some reason, you are unable to complete the workshop, please head to the [clean up](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/90-cleanup) steps. Resources created during the workshop may incur minor charges. It is best practice to spin down resources when they’re not in use.

**Congratulations!** You have successfully completed the Overview of the Environment.

Click “Next” to go to the next section.

## Running Jupyter Notebooks

Note

If you already know how to execute Jupyter notebooks, skip this section.

## [Running Notebook cells](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/20-environmentsetup/24-jupyternotebook#running-notebook-cells)

 1. When you open a notebook, you’ll see a popup that requires you to select a kernel and instance type. Please make sure that the Image is Data Science, Kernel is Python3 and Instance Type is ml.t3.medium as shown in the screenshot below.

![](https://cdn-images-1.medium.com/max/2000/0*C25beCgoggIDxK9I.png)

**Note:** If for some reason, you see an error on capacity for this particular instance type, it’s okay to scale up and choose the next available instance type.

 1. If you haven’t worked with Jupyter notebooks before, the following screenshots explains how to execute and run different cells.

![](https://cdn-images-1.medium.com/max/2820/0*3ORutIDCrL9SwLFB.png)

Clicking on the play button will execute the code within a selected cell.

 1. If you see a * sign next to a cell, it means that cell is still being executed, and you should wait. Once it finishes it will show a number where the * was.

![](https://cdn-images-1.medium.com/max/2000/0*4OSfATcPgrpYsWqP.png)

**Congratulations!** You have successfully completed the steps of how to run Jupyter Notebooks.

Click “Next” to go to the next section.

## Data Preparation

## [Overview](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/30-datapreparation#overview)

In this section, you will learn about the highlighted steps of the machine learning process.

![](https://cdn-images-1.medium.com/max/3044/0*nc3Llj3dPnr3Wlts.png)

## 1 — Ingest, Transform And Preprocess Data

Note

The following material provides contextual information about this lab. Please read through this information before you refer jupyter notebook for step-by-step code block instructions.

* [Overview](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/30-datapreparation/31-ingesttranformpreprocessjupyter#overview)

* [Instructions](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/30-datapreparation/31-ingesttranformpreprocessjupyter#instructions)

* [Data Transformation](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/30-datapreparation/31-ingesttranformpreprocessjupyter#data-transformation)

* [Data Visualization](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/30-datapreparation/31-ingesttranformpreprocessjupyter#data-visualization)

* [Conclusion](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/30-datapreparation/31-ingesttranformpreprocessjupyter#conclusion)

## [Overview](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/30-datapreparation/31-ingesttranformpreprocessjupyter#overview)

Exploratory Data Analysis (EDA) is an unavoidable step in the Machine Learning process. Raw data cannot be consumed directly to create a model. Data stakeholders understand, visualize and manipulate data before using it. Common transforms include (but aren’t limited to): removing symbols, one-hot encoding, removing outliers, and normalization.

## [Instructions](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/30-datapreparation/31-ingesttranformpreprocessjupyter#instructions)

You will be working on the first notebook in the series Lab_1_and_2-Data-Exploration-and-Features.ipynb. Please scroll down for important context before starting with the notebooks.

**The steps are outlined below:**

 1. Data visualization ~5m

 2. Data transformation ~8m

Total run time ~13 minutes

## [Data Transformation](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/30-datapreparation/31-ingesttranformpreprocessjupyter#data-transformation)

For our use case we have been provided with two datasets claims.csv and customers.csv containing the auto-insurance claims and customers' information respectively. This dataset was generated synthetically. However, the raw dataset can be non-numeric which is hard to visualize and cannot be used for the Machine Learning process.

Consider the columns driver_relationship or incident_type in claims.csv. The data type for values under these columns is known as an Object. It's a string that represents a feature. It's hard to use this kind of data directly since machines don't understand strings or what they represent. Instead, it would be a lot easier to just mark a feature as a one or zero.

![](https://cdn-images-1.medium.com/max/2000/0*eREF6Jl1_mQL_W3Y.png)

So instead of saying:

    driver_relationship = 'Spouse'

It’s better to break it out into another feature like so:

    driver_relationship_spouse = 1

We’ve elected to transform the data to get it ready for Machine Learning.

These columns will be one-hot encoded so that every type of collision can be a separate column.

![](https://cdn-images-1.medium.com/max/2000/0*rhJNh9yvWg_mBkcD.png)

Similarly, many transformations are required before the data can be used for Machine Learning. Data stakeholders often iterate over datasets multiple times before they can be used. In this case, transformations are created using Amazon SageMaker Data Wrangler (see the hint below). With this context in mind the following files are available:

 1. The .flow templates named customer_flow_template and claims_flow_template. These templates contain the transformations on customer and claims dataset created through SageMaker Data Wrangler. These files are in the standard JSON format and can be read in using the python json module.

 2. These transformations are applied to the raw datasets. The final processed datasets are claims_preprocessed.csv and customers_preprocessed.csv. **The notebook starts off with these preprocessed datasets.**

Hint

If you wish to learn how to make these transformations yourself, you can go through the [Bonus Labs section of this workshop titled — Data exploration using Amazon SageMaker Data Wrangler](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/95-bonusmaterial/91-bonus-datawrangler)

## [Data Visualization](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/30-datapreparation/31-ingesttranformpreprocessjupyter#data-visualization)

At this point, let’s head over to the first notebook. Navigate to the SageMaker Studio UI and click on the folder icon on the left navigation panel. Open the folder FraudDetectionWorkshop. Finally, open the first notebook titled Lab_1_and_2-Data-Exploration-and-Features.ipynb.

![](https://cdn-images-1.medium.com/max/2000/0*XU7wCKwwJO3wrIQy.png)

Note

Follow the jupyter notebook instructions till you complete Lab 1 and navigate back here when done.

## [Conclusion](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/30-datapreparation/31-ingesttranformpreprocessjupyter#conclusion)

**Congratulations!** You’ve successfully learned how to visualize and pre-process the data and gather insights.

In this lab we learned how to transform data easily using Amazon SageMaker Studio Notebooks.

Click “Next” to go to the next section.

## 2 — Feature Engineering

Note

The following material provides contextual information about this lab. Please read through this information before you refer jupyter notebook for step-by-step code block instructions.

Prerequisite

Please make sure Lab 1 is executed successfully before you proceed with this lab.

* [Overview](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/30-datapreparation/32-storefeaturesfeaturestore#overview)

* [Instructions](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/30-datapreparation/32-storefeaturesfeaturestore#instructions)

* [Creating the Feature Store](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/30-datapreparation/32-storefeaturesfeaturestore#creating-the-feature-store)

* [Split the dataset and upload to S3](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/30-datapreparation/32-storefeaturesfeaturestore#split-the-dataset-and-upload-to-s3)

* [Conclusion](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/30-datapreparation/32-storefeaturesfeaturestore#conclusion)

## [Overview](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/30-datapreparation/32-storefeaturesfeaturestore#overview)

[Amazon SageMaker Feature Store ](https://docs.aws.amazon.com/sagemaker/latest/dg/feature-store.html)provides a central repository for data features with low latency (milliseconds) reads and writes. Features can be stored, retrieved, discovered, and shared through SageMaker Feature Store for easy reuse across models and teams with secure access and control.

SageMaker Feature Store keeps track of the metadata of stored features (e.g. feature name or version number) so that you can query the features for the right attributes in batches or in real time using [Amazon Athena ](https://aws.amazon.com/athena/), an interactive query service.

In this lab, you will learn how to use Amazon SageMaker Feature Store to store and retrieve machine learning (ML) features.

## [Instructions](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/30-datapreparation/32-storefeaturesfeaturestore#instructions)

**The steps are outlined below:**

 1. Creating the Feature Store ~6 min (including time to create and ingest data on Feature Store).

 2. Visualize Feature Store ~2 min.

 3. Upload data to S3 ~1 min.

Total run time ~10 minutes.

## [Creating the Feature Store](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/30-datapreparation/32-storefeaturesfeaturestore#creating-the-feature-store)

The collected data, we refer to it as raw data is typically not ready to be consumed by ML Models, The data needs to transformed e.g. encoding, dealing with missing values, outliers, aggregations. This process is known as feature engineering and the signals that are extracted as part of this data prep are referred to as features.

A feature group is a logical grouping of features and these groups consist of features that are computed together, related by common parameters, or are all related to the same business domain entity.

In this step, you are going to create two feature groups: customer and claims.

![](https://cdn-images-1.medium.com/max/2000/1*B_Xl8Lv3ei6TbYNab29k2w.png)

After the Feature Groups have been created, we can put data into each store by using the [PutRecord API ](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_feature_store_PutRecord.html). This API can handle high TPS (Transactions Per Second) and is designed to be called concurrently by different streams. The data from PUT requests is written to the offline store within few minutes of ingestion.

Hint

It is possible to verify that the data is available offline by navigating to the S3 Bucket.

## [Split the Dataset and upload to S3](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/30-datapreparation/32-storefeaturesfeaturestore#split-the-dataset-and-upload-to-s3)

Once the data is available in the offline store, it will automatically be cataloged and loaded into an [Amazon Athena ](https://aws.amazon.com/pt/athena/)table (this is done by default, but can be turned off). In order to build our training and test datasets, you will submit a SQL query to join the Claims and Customers tables created in Athena.

The last step in this notebook is to upload newly created datasets into S3.

At this point, let’s navigate back to the first notebook (Lab_1_and_2-Data-Exploration-and-Features.ipynb) and scroll down to **Lab 2: Feature Engineering**

Note

Follow the jupyter notebook instructions till you complete Lab 2 and navigate back here when done.

## [Conclusion](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/30-datapreparation/32-storefeaturesfeaturestore#conclusion)

**Congratulations!** You have successfully prepared the data to train an XGBoost model.

In this lab we learned how to ingest features into Amazon SageMaker Feature Store and prepare our data for training.

Click “Next” to go to the next section.

## Training and Deployment

## [Overview](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/40-traininganddeployment#overview)

In this section, you will learn about the following highlighted step of the Machine Learning process.

![](https://cdn-images-1.medium.com/max/3508/1*BDbbYEwQUtoIJPExSRZO3Q.png)

## 3 — Train a Model using XGBoost

Note

The following material provides contextual information about this lab. Please read through this information before you refer jupyter notebook for step-by-step code block instructions.

Prerequisite

Please make sure Lab 2 is executed successfully before you proceed with this lab.

* [Overview](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/40-traininganddeployment/41-trainandtune#overview)

* [Instructions](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/40-traininganddeployment/41-trainandtune#instructions)

* [Data Handling](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/40-traininganddeployment/41-trainandtune#data-handling)

* [Train a Model using XGBoost](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/40-traininganddeployment/41-trainandtune#train-a-model-using-xgboost)

* [Conclusion](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/40-traininganddeployment/41-trainandtune#conclusion)

## [Overview](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/40-traininganddeployment/41-trainandtune#overview)

In this lab, you will learn how to use [Amazon SageMaker Training Job ](https://docs.aws.amazon.com/sagemaker/latest/dg/how-it-works-training.html)to build, and train the ML model.

To train a model using SageMaker, you create a training job. The training job includes the following information:

* The URL of the Amazon Simple Storage Service (Amazon S3) bucket where you’ve stored the training data.

* The compute resources that you want SageMaker to use for model training. Compute resources are ML compute instances that are managed by SageMaker.

* The URL of the S3 bucket where you want to store the output of the job.

* The Amazon Elastic Container Registry path where the docker container image is stored.

For this tutorial, you will use the [XGBoost Open Source Framework ](https://sagemaker.readthedocs.io/en/stable/frameworks/xgboost/xgboost.html)to train your model. This estimator is accessed via the SageMaker SDK, but mirrors the open source version of the [XGBoost Python package ](https://xgboost.readthedocs.io/en/latest/python/index.html). Any functionality provided by the XGBoost Python package can be implemented in your training script. XGBoost is an extremely popular, open-source package for gradient boosted trees. It is computationally powerful, fully featured, and has been successfully used in many machine learning competitions.

## [Instructions](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/40-traininganddeployment/41-trainandtune#instructions)

**The steps are outlined below:**

 1. Data handling ~1m

 2. Train a model using XGBoost ~8m (including running the training code ~4m)

 3. Deposit the model in SageMaker Model Registry ~3m

Total run time ~ 12 mins.

## [Data handling](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/40-traininganddeployment/41-trainandtune#data-handling)

There are two ways to obtain the dataset:

 1. Use the dataset you uploaded to Amazon S3 bucket in the previous Lab (Lab 2 — Feature Engineering).

 2. Upload the following datasets from data folder to Amazon S3: train.csv, test.csv

The following code upload the datasets from data folder to Amazon S3:

![](https://cdn-images-1.medium.com/max/3032/1*0klC4UdI58VUwq9zfTKvkg.png)

## [Train a model using XGBoost](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/40-traininganddeployment/41-trainandtune#train-a-model-using-xgboost)

You will define SageMaker Estimator using [XGBoost Open Source Framework ](https://sagemaker.readthedocs.io/en/stable/frameworks/xgboost/xgboost.html)to train your model. The following code will create the Estimator object and start the training job using xgb_estimator.fit() function call.

![](https://cdn-images-1.medium.com/max/3442/1*W4_XLALZ5MTxocVf2DtmEw.png)

For this example, we will use the following parameters for the XGBoost estimator:

* entry_point - Path to the Python source file which should be executed as the entry point to training.

* hyperparameters - Hyperparameters that will be used for training. The hyperparameters are made accessible as a dict[str, str] to the training code on SageMaker.

* output_path - S3 location for saving the training result (model artifacts and output files).

* framework_version - XGBoost version you want to use for executing your model training code.

* instance_type - Type of EC2 instance to use for training.

If you want to explore the breadth of functionality offered by the SageMaker XGBoost Framework you can read about all the configuration parameters by referencing the inheriting classes. The XGBoost class inherits from the Framework class and Framework inherits from the EstimatorBase class:

* [XGBoost Estimator documentation](https://sagemaker.readthedocs.io/en/stable/frameworks/xgboost/xgboost.html#sagemaker.xgboost.estimator.XGBoost)

* [Framework documentation](https://sagemaker.readthedocs.io/en/stable/api/training/estimators.html#sagemaker.estimator.Framework)

* [EstimatorBase documentation](https://sagemaker.readthedocs.io/en/stable/api/training/estimators.html#sagemaker.estimator.EstimatorBase)

Launching a training job and storing the trained model into S3 should take ~4 minutes. Notice that the output includes the value of Billable seconds, which is the amount of time you will be actually charged for.

![](https://cdn-images-1.medium.com/max/3402/1*KoKE1eNjNtFRKjB0PMdrnQ.png)

## [Deposit the model in SageMaker Model Registry](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/40-traininganddeployment/41-trainandtune#deposit-the-model-in-sagemaker-model-registry)

After the successful training job, you can register the trained model in [SageMaker Model Registry ](https://docs.aws.amazon.com/sagemaker/latest/dg/model-registry.html). SageMaker’s Model Registry is a metadata store for your machine learning models. Within the model registry, models are versioned and registered as model packages within model groups. Each model package contains an Amazon S3 URI to the model files associated with the trained model and an Amazon ECR URI that points to the container used while serving the model.

At this point, let’s navigate back to the training notebook (Lab_3_and_4-Training_and_Deployment.ipynb) and scroll down to **Lab 3: Prerequisites**

Note

Follow the jupyter notebook instructions till you complete Lab 3 and navigate back here when done.

## [Conclusion](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/40-traininganddeployment/41-trainandtune#conclusion)

**Congratulations!** You have successfully built and trained your model.

In this lab you have walked through the process of building, and training XGBoost model using Amazon SageMaker Estimator. You also used the SageMaker Python SDK to train the model.

Click “Next” to go to the next section.

## 4 — Deploy and Serve the Model

Note

The following material provides contextual information about this lab. Please read through this information before you refer jupyter notebook for step-by-step code block instructions.

Prerequisite

Please make sure Lab 3 is executed successfully before you proceed with this lab.

* [Overview](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/40-traininganddeployment/42-deploy#overview)

* [Instructions](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/40-traininganddeployment/42-deploy#instructions)

* [Conclusion](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/40-traininganddeployment/42-deploy#conclusion)

## [Overview](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/40-traininganddeployment/42-deploy#overview)

After you train your machine learning model, you can deploy it using Amazon SageMaker to get predictions in any of the following ways, depending on your use case:

* For persistent, real-time endpoints that make one prediction at a time, use SageMaker real-time hosting services.

* Workloads that have idle periods between traffic spurts and can tolerate cold starts, use Serverless Inference.

* Requests with large payload sizes up to 1GB, long processing times, and near real-time latency requirements, use Amazon SageMaker Asynchronous Inference.

* To get predictions for an entire dataset, use SageMaker batch transform.

Following image describes different deployment options and their use cases.

![](https://cdn-images-1.medium.com/max/2632/1*z1PFqflbHwTSY1OEfWrwbQ.png)

## [Instructions](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/40-traininganddeployment/42-deploy#instructions)

**The steps are outlined below:**

* Evaluate trained model and update status in the model registry: ~3 mins

* Model deployment: ~1 min

* Create/update endpoint: 5 mins

* Predictor interface: 1 mins

Total run time ~ 10 mins.

## [Evaluate trained model](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/40-traininganddeployment/42-deploy#evaluate-trained-model)

After you create a model version, you typically want to evaluate its performance before you deploy the model in production. If it performs to your requirements, you can update the approval status of the model version to Approved. In the real-life MLOps lifecycle, a model package gets approved after evaluation by data scientists, subject matter experts, and auditors.

For the purpose of this lab, we will evaluate the model with test dataset that was created during training process. The lab contains evaluate.py script that calculates AUC (Area under the ROC Curve) on the test dataset. The AUC threshold is set at 0.7. If the test dataset AUC is below the threshold, then the approval status should be “Rejected” for that model version.

## [Model deployment](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/40-traininganddeployment/42-deploy#model-deployment)

To prepare the model for deployment, you will conduct following steps:

* Query the model registry and list all the model versions:

* Hint

* For the purpose of this lab, we will get the latest version of the model from the model registry. However, you can apply different filtering criterion such as listing approved models or get specific version of the model. Please refer to the [Model Registry ](https://docs.aws.amazon.com/sagemaker/latest/dg/model-registry.html)documentation.

* Define the endpoint configuration: Specify the name of one or more models in production (variants) and the ML compute instances that you want SageMaker to launch to host each production variant.

![](https://cdn-images-1.medium.com/max/3652/1*oWQn3XChAEIUyBvUzkoqgw.png)

When hosting models in production, you can configure the endpoint to elastically scale the deployed ML compute instances. For each production variant, you specify the number of ML compute instances that you want to deploy. When you specify two or more instances, SageMaker launches them in multiple Availability Zones, this ensures continuous availability. SageMaker manages deploying the instances.

## [Create/update endpoint](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/40-traininganddeployment/42-deploy#createupdate-endpoint)

Once you have your model and endpoint configuration, use the [CreateEndpoint API ](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_CreateEndpoint.html)to create your endpoint. Provide the endpoint configuration to SageMaker. The service launches the ML compute instances and deploys the model or models as specified in the configuration. Please refer to the [documentation ](https://docs.aws.amazon.com/sagemaker/latest/dg/realtime-endpoints-deployment.html).

## [Predictor interface](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/40-traininganddeployment/42-deploy#predictor-interface)

In this part of the workshop, you will use the data from dataset.csv to run inference against the newly deployed endpoint.

At this point, let’s navigate back to the training notebook (Lab_3_and_4-Training_and_Deployment.ipynb) and scroll down to **Lab 4: Deploy and serve the model**

Note

Follow the jupyter notebook instructions till you complete Lab 4 and navigate back here when done.

## [Conclusion](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/40-traininganddeployment/42-deploy#conclusion)

**Congratulations!** You have successfully deployed an endpoint to get predictions from your model.

In this lab, you created a low latency Endpoint using Amazon SageMaker and deployed your model to get predictions. In the next lab, you will learn how to integrate all of the steps you’ve learnt so far using SageMaker Pipelines.

Click “Next” to go to the next section.

## Machine Learning Workflow

## [Overview](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines#overview)

In this section, you will learn about the following highlighted step of the Machine Learning process.

![](https://cdn-images-1.medium.com/max/4708/1*ckia5k9AJ343cPk_5eh77A.png)

## 5 — Pipelines

Note

The following material provides contextual information about this lab. Please read through this information before you refer jupyter notebook for step-by-step code block instructions.

Attention

This lab demonstrates how to build an end-to-end machine learning workflow using Sagemaker Pipeline. This is a stand-alone lab and can be run independently of the previous labs.

If you have already executed the previous labs (Lab 1 and Lab 2) then you don’t need to run the **Step 0** on juypter notebook.

## [Content](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#content)

* [Overview](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#overview)

* [Instructions](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#instructions)

* [Create Automated Machine Learning Pipeline](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#create-automated-machine-learning-pipeline)

* [Step 1 — Data Wrangler Preprocessing](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#step-1-data-wrangler-preprocessing)

* [Step 2 — Create Dataset and Train/Test Split](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#step-2-create-dataset-and-traintest-split)

* [Step 3 — Train XGBoost Model](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#step-3-train-xgboost-model)

* [Step 4 — Model Pre-Deployment Step](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#step-4-model-pre-deployment)

* [Step 5 — Register Model](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#step-5-register-model)

* [Step 6 — Model deployment](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#step-6-model-deployment)

* [Step 7 — Combine the Pipeline Steps](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#step-7-combine-the-pipeline-steps)

* [Create the pipeline definition](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#create-the-pipeline-definition)

* [Review the pipeline definition](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#review-the-pipeline-definition)

* [Run the pipeline](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#run-the-pipeline)

## [Overview](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#overview)

In previous labs, you built separate processes for data preparation, training, and deployment. In this lab, you will build a machine learning workflow using SageMaker Pipelines that automates end-to-end process of data preparation, model training, and model deployment to detect fraudulent automobile insurance claims.

![](https://cdn-images-1.medium.com/max/2224/0*neHJXSNBdo--kzTO.png)

## [Instructions](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#instructions)

**The machine learning workflow steps are outlined below:**

* Step 1 — Data Wrangler Preprocessing ~2 min

* Step 2 — Create Dataset and Train/Test Split ~1 min

* Step 3 — Train XGBoost Model ~1 min

* Step 4 — Model Pre-Deployment Step ~1 min

* Step 5 — Register Model ~1 min

* Step 6 — Model deployment ~1 min

* Step 7 — Combine and Run the Pipeline Steps ~1 min

* Run the pipeline ~15 mins

Total run time ~ 23 mins.

## [Create Automated Machine Learning Pipeline](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#create-automated-machine-learning-pipeline)

SageMaker Pipelines service is composed of following steps. These steps define the actions that the pipeline takes and the relationships between steps using properties.

### [Step 1 — Data Wrangler Preprocessing](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#step-1-data-wrangler-preprocessing)

Define Data Wrangler inputs using ProcessingInput, outputs using ProcessingOutput, and Processing Step to create a job for data processing for "claims" and "customer" data.

### [Step 2 — Create Dataset and Train/Test Split](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#step-2-create-dataset-and-traintest-split)

Next you will create an instance of a SKLearnProcessor processor. You can split the dataset without using SKLearnProcessor as well, but if the dataset is larger than the one provided, it will takes more time and requires local compute resources. Hence it is recommended to use manage processing job.

### [Step 3 — Train XGBoost Model](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#step-3-train-xgboost-model)

You will use SageMaker’s XGBoost algorithm to train the dataset using the [Estimator]([https://sagemaker.readthedocs.io/en/stable/api/training ](https://sagemaker.readthedocs.io/en/stable/api/training)estimators.html) interface. A typical training script loads data from the input channels, configures training with hyperparameters, trains a model, and saves the model to “model_dir”.

### [Step 4 — Model Pre-Deployment](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#step-4-model-pre-deployment)

sagemaker.model.Model denotes a SageMaker Model that can be deployed to an Endpoint.

### [Step 5 — Register Model](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#step-5-register-model)

Typically, customers can create a ModelPackageGroup for SageMaker Pipelines so that model package versions are added for every iteration.

### [Step 6 — Model deployment](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#step-6-model-deployment)

Once the model is registered, the next step is deploying the model. You will use Lambda function step to deploy the model as real time endpoint. The SageMaker SDK provides a Lambda helper class that can be used to create a Lambda function. This function is provided to the Lambda step for invocation via the pipeline. Alternatively, a predefined Lambda function can also be provided to the Lambda step.

Attention

Please open [CloudFormation console ](https://console.aws.amazon.com/cloudformation/home)and copy Lambda ARN of the lambda function (under the Outputs tab).

![](https://cdn-images-1.medium.com/max/3548/0*FOZit2AzuGEJm3Qn.png)

Copy lambda function ARN value and add it to cell #21

![](https://cdn-images-1.medium.com/max/3380/0*OkpnFlpKHePPsRGf.png)

### [Step 7 — Combine the Pipeline Steps](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#step-7-combine-the-pipeline-steps)

SageMaker Pipelines is a series of interconnected workflow steps that are defined using the [Pipelines SDK ](https://sagemaker.readthedocs.io/en/stable/workflows/pipelines/sagemaker.workflow.pipelines.html). This Pipelines definition encodes a pipeline using a directed acyclic graph (DAG) that can be exported as a JSON definition.

## [Create the pipeline definition](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#create-the-pipeline-definition)

Submit the pipeline definition to the SageMaker Pipelines to either create a new pipeline if it doesn’t exist, or update the existing pipeline if it does.

![](https://cdn-images-1.medium.com/max/3844/0*xcaMrhxAhaTLPP0S.png)

## [Review the pipeline definition](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#review-the-pipeline-definition)

Describing the pipeline status ensures that it has been created successfully. Viewing the pipeline definition with all the string variables interpolated may help debug pipeline bugs.

![](https://cdn-images-1.medium.com/max/3840/0*ttR-VlHnkHllkYjk.png)

## [Run the pipeline](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#run-the-pipeline)

Start a pipeline execution. Note this will take about 15 minutes to complete. You can watch the progress of the Pipeline Job on your SageMaker Studio Pipelines panel.

 1. Click the Home folder pointed by the arrow and click on Pipelines.

 2. You will see the available pipelines in the table on the right.

 3. Click on FraudDetectDemo.

![](https://cdn-images-1.medium.com/max/3760/0*Wk1h61OJNRDhlCgW.png)

Next, you will see the executions listed on the next page. Double-click on the Status executing to be taken to the graph representation.

![](https://cdn-images-1.medium.com/max/2484/0*XfeutYaOj-NbEe1k.png)

You will see the nodes turn green when the corresponding steps are complete.

![](https://cdn-images-1.medium.com/max/3200/0*jA6ruuP03WUm8bWo.png)

Note

Follow the jupyter notebook instructions till you complete Lab 5 and navigate back here when done.

## [Conclusion](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/50-pipelines/51-pipelines#conclusion)

**Congratulations!** You have successfully created an end to end machine learning workflow using SageMaker Pipelines.

Click “Next” to go to the next section.

## Summary

## [What you have learned](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/60-summary#what-you-have-learned)

In this workshop, you have learned how to:

* Inspect, analyze and transform an auto insurance fraud dataset

* Ingest transformed data into SageMaker Feature Store using the SageMaker Python SDK

* Train an XGBoost model using SageMaker Training Jobs

* Create a realtime endpoint for low latency requests using SageMaker

* Integrate all previous steps into an MLOps workflow with SageMaker Pipelines

## [Thank you!](https://catalog.workshops.aws/sagemaker-fraud-detection/en-US/60-summary#thank-you!)

## Clean Up

Congratulations on developing an ML fraud detection solution and deploying automated pipelines!

Attention

If you are at an AWS event, such as re:Invent or an Immersion Day, and are using an AWS provided account, then you don’t need to worry about cleaning up the resources.

To clean up resources, please do the following:

 1. Delete the CloudFormation stack to clean up the environment.

 2. Go to [CloudFormation ](https://console.aws.amazon.com/cloudformation/home)home page, click **Stacks **under the left hand side menu, select stack **fraud-detection-workshop **stack, and click **Delete** button to delete the stack.

![](https://cdn-images-1.medium.com/max/2542/0*AaMEUYVU3ewny4XM.png)

 1. Delete the Model.

 2. During Lab 4, we deleted the SageMaker hosted endpoint but not the model. We needed that model for Detect Bias bonus lab execution. Go to [SageMaker ](https://console.aws.amazon.com/sagemaker/home)home page and expand **Inference **in SageMaker dashboard section on left hand side menu. Click **Models**, and select **fraud-detect-model-xxxxxxxxxxxx**. Click **Action **button and select **Delete** option to delete the model.

![](https://cdn-images-1.medium.com/max/2222/0*wTJmB_hvtFjUWXk4.png)

 1. Delete the Endpoint Configuration.

 2. In SageMaker home page left hand side menu, expand **Inference** and click on **Endpoint configurations**. Select **fraud-detect-demo-endpoint-config-xxxxxxxxxxxx** configuration, click **Actions** button, and select **Delete** option to delete the configuration.

![](https://cdn-images-1.medium.com/max/2590/0*Gbm23iB3A-SXDbNj.png)

 1. Delete the lifecycle configuration.

 2. In SageMaker home page left hand side menu, click on **Lifecycle configurations**. Select **git-clone-step** lifecycle configuration and click **Delete** button to delete the lifecycle configuration.

![](https://cdn-images-1.medium.com/max/2014/0*yTpyjpNt-WzGQQqY.png)

 1. And, finally delete the S3 bucket.

 2. Go to [S3 ](https://console.aws.amazon.com/sagemaker/home). To delete the bucket, you need to first delete the objects inside the bucket. Click on **sagemaker — xxxxxxxxxxxx** bucket and select checkbox on the top of the object table to select all objects.

![](https://cdn-images-1.medium.com/max/2192/0*A9zT9wZCKX_6AcOD.png)

 1. Click **Delete** button to delete all objects.

 2. Navigate back to S3 buckets list, select **sagemaker — xxxxxxxxxxxx** bucket and click **Delete** button to delete the bucket.

![](https://cdn-images-1.medium.com/max/2198/0*m2chZEcBnOJWuAtu.png)

**Congratulations!** You have successfully cleaned up the environment.

This brings us to the end of this workshop.

Thank you.

## Challenges Faced and Solutions

**Challenge 1: Real-Time Model Inference and Latency Optimization**

* **Solution**: Leveraged API Gateway and Lambda to manage requests, reducing latency by preprocessing data in Lambda and only sending necessary data to SageMaker.

**Challenge 2: Managing Security for Sensitive Data**

* **Solution**: Used AWS Secrets Manager to secure sensitive information such as database credentials, API keys, and integrated with IAM to enforce role-based access control.

**Challenge 3: Monitoring and Troubleshooting Complex Workflows**

* **Solution**: Integrated CloudWatch, CloudTrail, and X-Ray to gain visibility into all workflow steps, allowing for efficient troubleshooting and resource optimization.

## Conclusion

This end-to-end solution highlights the power of Amazon SageMaker in handling real-time fraud detection and anomaly classification. By integrating AWS tools for automation, monitoring, and security, this project demonstrates an adaptable, high-performance architecture that can scale to meet growing data demands. The setup is versatile and supports businesses in proactive fraud management, ensuring fast, accurate, and secure anomaly detection for production-grade applications.

To explore and experiment with the project’s code and documentation, visit the [**GitHub Repository](https://github.com/Dark-Cookie/AWS-Projects/tree/main/Level%20400/10.%20Deploying%20a%20Complete%20Machine%20Learning%20Fraud%20Detection%20Solution%20Using%20Amazon%20SageMaker)**. Here you can access the complete code, follow along with detailed instructions, and customize the applications to fit your own use cases.
>  ***Asif Khan — Aspiring Cloud Architect | Weekly Cloud Learning Chronicler***

[**LinkedIn](https://www.linkedin.com/in/asif0108/)**/[**Twitter](https://x.com/asif26073)**/[**GitHub](https://github.com/Dark-Cookie)**
