# OPS04-AWS200 - Create a CloudWatch Alarm

## Cloud Service Provider
- Amazon Web Services

## Difficulty
- Level 200 (Intermediate)

## Project's Author(s)
- [@andrewbrown](https://twitter.com/andrewbrown)

## Objectives

### You need to complete the following:
- Launch an EC2 t2.micro instance with a public IP address and supply the [provided bash script](OPS04-AWS200-userdata.sh) to install a simple website with an apache server in the UserData.
- Visit the the public IP so that you are generating NetworkIn. You need
  to do this so the Metric appears selectable when create your
CloudWatch Alarm
- Create a CloudWatch Alarm and use EC2 NetworkIn as the metric
- Set your CloudWatch Alarm to use a 5 minute period
- Set your CloudWatch Alarm to a very low static threshold such as 5000
- Set the Datapoint to alarms to 3 of 4
- Try to get the Alarm to trigger an Alert state by visiting the website
  and generating NetworkIN

### You need to answer the following:

## What is a CloudWatch Alarm?
A **CloudWatch Alarm** is a monitoring feature in AWS CloudWatch that allows you to set predefined conditions on metrics. When a metric exceeds or drops below a specified threshold, the alarm is triggered and performs a defined action (such as sending an email via SNS or executing an automated action).

For example, you can set a CloudWatch alarm on the **CPUUtilization** metric of an EC2 instance. When CPU utilization exceeds 80% over a certain period, the alarm will enter the **ALARM** state, notifying you of the high resource usage.

## What is a Metric?
A **metric** in AWS is a time-ordered set of data points that captures specific resource usage or performance over time. Metrics are used to track various parameters of your AWS resources, such as CPU utilization, disk read/write operations, and network traffic.

AWS services (like EC2, RDS, Lambda, etc.) provide predefined metrics, but you can also create **custom metrics** to track specific application data.

Example metrics:
- **NetworkIn**: The amount of data received by an EC2 instance over the network.
- **CPUUtilization**: The percentage of allocated compute resources being used by an EC2 instance.

## What do we mean when we say "breach"?
A **breach** refers to the moment when the value of a monitored metric surpasses or falls below the defined threshold for the alarm. This could indicate that something unexpected is happening with your resources, like a sudden spike in network traffic or CPU utilization, potentially leading to performance degradation or failures.

For instance, if you have set a threshold of 5000 bytes for **NetworkIn**, a breach would occur when the metric value exceeds 5000 bytes during the specified evaluation period.

## What is a Threshold?
A **threshold** is the defined limit or value at which the CloudWatch Alarm should trigger a change in state. When the metric value crosses this threshold, the alarm enters the **ALARM** state, signaling that action may be required.

Example: If the **CPUUtilization** threshold is set to 80%, the alarm will trigger when the instance's CPU usage exceeds 80% over the defined period.

## What is a Data Point?
A **data point** represents a single measurement of a metric during a specific period. Metrics consist of a series of these data points, which are collected over time to monitor performance and resource usage.

For example, if the **NetworkIn** metric is evaluated every 5 minutes, a data point will be collected every 5 minutes, reflecting the total network traffic for that period.

## What is a Period?
A **period** is the interval of time over which a single data point is aggregated for a metric. CloudWatch collects metrics at a set period, and each data point represents an average, sum, or count of values during this time frame.

Example: If the period is set to **5 minutes**, CloudWatch aggregates data for 5 minutes and records a data point at the end of that period.

## What are Evaluation Periods?
**Evaluation periods** refer to the number of consecutive periods that CloudWatch uses to evaluate the metric before triggering an alarm. This prevents alarms from being triggered by short-term metric spikes that aren't significant.

For example, if you set 3 evaluation periods of 5 minutes each (i.e., 3 out of 4 datapoints), CloudWatch will evaluate the metric for 15 minutes before deciding to trigger the alarm if the threshold is breached in 3 of those periods.

## References
- [NetworkIN Instance Metric](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/viewing_metrics_with_cloudwatch.html#ec2-cloudwatch-metrics)
- [Using Amazon CloudWatch Alarms](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html)

## Costs
- t2.micro is included in the Free Tier
- First 10 CloudWatch Alarms are included in the Free Tier

## Estimated time to complete
- 45 minutes

## Tips
- It takes EC2 5 minutes before it reports NetworkIN so expect to wait
  5-10 mins after visiting the website intially

## Output
![{173A53AD-AE5D-4C09-A295-59238DA4DD09}](https://github.com/shubhammurti/AWS-Projects-Portfolio/blob/03ee878799e734e51d9f9d2a6fa93efb9ae1f53e/Level%20200/6.%20Create%20a%20CloudWatch%20Alarm/Image.png)
