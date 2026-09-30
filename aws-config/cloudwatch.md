# Amazon CloudWatch Configuration

## Overview

Amazon CloudWatch was used to monitor the EC2 instances and Auto Scaling activity in this project.

CloudWatch provides metrics and alarms that help monitor CPU utilization and scaling conditions.

## Monitoring

The main metric used for the Auto Scaling setup is:

```text
CPUUtilization
```

The Auto Scaling Group uses a Target Tracking policy with a target average CPU utilization of **50%**.

## Alarms

CloudWatch alarms associated with the Target Tracking scaling policy provide visibility into the conditions used by Auto Scaling.

![CloudWatch Alarms](../screenshots/07-cloudwatch-alarms.png)

## Monitoring Flow

```text
EC2 CPU Utilization
        |
        v
     CloudWatch
        |
        v
   Alarm / Policy
        |
        v
 Auto Scaling Group
```

## Related Components

- Amazon EC2
- Auto Scaling Group
- Target Tracking Policy
- Amazon SNS
