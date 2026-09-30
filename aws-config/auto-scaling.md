# Auto Scaling Group Configuration

## Overview

An Amazon EC2 Auto Scaling Group (ASG) was configured to automatically manage the number of EC2 instances based on application workload.

The ASG works together with the Application Load Balancer and Target Group to provide scalable application infrastructure.

## Configuration

| Setting | Value |
|---|---|
| Auto Scaling Group | ASG-1 |
| Minimum capacity | 2 |
| Desired capacity | 2 |
| Maximum capacity | 3 |
| Scaling policy | Target Tracking |
| Target CPU utilization | 50% |

## Scaling Policy

A Target Tracking scaling policy was configured with a target average CPU utilization of **50%**.

When the average CPU utilization increases and additional capacity is required, the Auto Scaling Group can launch an additional EC2 instance.

When demand decreases, the Auto Scaling Group can reduce capacity while maintaining the configured minimum of 2 instances.

## Scaling Flow

```text
Application Load
       |
       v
EC2 CPU Utilization
       |
       v
CloudWatch Metrics
       |
       v
Target Tracking Policy
       |
       v
Auto Scaling Group
       |
       +----> Launch EC2 instance
       |
       +----> Reduce EC2 capacity
