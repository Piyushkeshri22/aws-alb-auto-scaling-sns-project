# AWS ALB + Auto Scaling + CloudWatch + SNS

## Project Overview

This project demonstrates a highly available and scalable web application infrastructure on AWS.

The application is deployed on Amazon EC2 instances and exposed through an Application Load Balancer (ALB). An Auto Scaling Group automatically adjusts the number of EC2 instances based on CPU utilization.

Amazon CloudWatch is used for monitoring, while Amazon SNS is configured to send notifications for relevant monitoring events.

## Architecture

User
  |
  v
Application Load Balancer (ALB)
  |
  v
Target Group
  |
  v
Auto Scaling Group
  |
  +------------------+
  |                  |
  v                  v
EC2 Instance 1    EC2 Instance 2
  |
  v
CloudWatch
  |
  v
SNS
  |
  v
Email Notification

## AWS Services Used

- Amazon EC2
- Application Load Balancer (ALB)
- Target Group
- Launch Template
- Auto Scaling Group (ASG)
- Amazon CloudWatch
- Amazon SNS
- Amazon VPC

## Key Features

- Application traffic distributed through an Application Load Balancer
- EC2 instances managed using an Auto Scaling Group
- Target Tracking scaling policy configured for 50% average CPU utilization
- Automatic scale-out and scale-in based on workload
- CloudWatch monitoring and alarms
- SNS email notifications
- EC2 instances distributed across multiple Availability Zones

## Implementation

### 1. EC2 Instances

Created EC2 instances to host the web application.

The instances were configured in different Availability Zones to improve availability.

### 2. Launch Template

Created a Launch Template containing the configuration required to launch EC2 instances.

The template is used by the Auto Scaling Group when additional instances are required.

### 3. Target Group

Created a Target Group and registered EC2 instances as targets.

The Target Group allows the Application Load Balancer to distribute incoming traffic to healthy instances.

### 4. Application Load Balancer

Configured an Application Load Balancer to receive incoming HTTP traffic and forward requests to the Target Group.

### 5. Auto Scaling Group

Created an Auto Scaling Group to manage the EC2 instances.

The ASG maintains the required number of instances and launches or terminates instances according to the scaling policy.

### 6. Target Tracking Scaling

Configured a Target Tracking policy with:

**Target CPU Utilization: 50%**

When the average CPU utilization increases above the target, the Auto Scaling Group can launch additional EC2 instances.

When the workload decreases, the ASG can reduce the number of instances.

### 7. CloudWatch Monitoring

Amazon CloudWatch was used to monitor EC2 CPU utilization and scaling-related metrics.

CloudWatch alarms were configured to monitor the environment.

### 8. SNS Notifications

Amazon SNS was configured to provide email notifications for monitoring events.

This allows important infrastructure events to be communicated without continuously checking the AWS console.

## Scaling Demonstration

The project demonstrates Auto Scaling by increasing the number of EC2 instances when workload conditions require additional capacity.

Example:

```text
Initial Capacity
      |
      v
2 EC2 Instances
      |
      | Increased workload
      v
Auto Scaling
      |
      v
Additional EC2 Instances
