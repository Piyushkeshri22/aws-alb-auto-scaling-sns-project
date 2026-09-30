# AWS ALB + Auto Scaling + CloudWatch + SNS

## Project Overview

This project demonstrates a scalable and highly available web application infrastructure built using AWS.

The application is hosted on Amazon EC2 instances and exposed through an Application Load Balancer (ALB). An Auto Scaling Group (ASG) automatically manages EC2 capacity based on CPU utilization.

Amazon CloudWatch is used for monitoring and alarms, while Amazon SNS is configured to send email notifications.

---

## Architecture

![AWS Architecture](architecture/architecture.png)

### Traffic Flow

```text
User
  |
  v
Application Load Balancer
  |
  v
Target Group
  |
  v
EC2 Instances managed by Auto Scaling Group
