# AWS ALB + Auto Scaling + CloudWatch + SNS

## Project Overview

This project demonstrates a scalable and highly available web application infrastructure built using AWS.

The application is hosted on Amazon EC2 instances and exposed through an Application Load Balancer (ALB). An Auto Scaling Group (ASG) automatically adjusts the number of EC2 instances based on CPU utilization.

Amazon CloudWatch is used for monitoring and alarms, while Amazon SNS is configured to send email notifications.

## Architecture

![AWS Architecture](architecture/architecture.png)

### Traffic and Monitoring Flow

User → Application Load Balancer → Target Group → EC2 Instances

CloudWatch → SNS → Email Notification

## AWS Services Used

- **Amazon EC2** – Hosts the web application
- **Application Load Balancer (ALB)** – Distributes incoming traffic
- **Target Group** – Registers and performs health checks on EC2 instances
- **Launch Template** – Defines EC2 instance configuration
- **Auto Scaling Group (ASG)** – Automatically manages EC2 capacity
- **Amazon CloudWatch** – Monitors CPU utilization and scaling activity
- **Amazon SNS** – Sends email notifications
- **Amazon VPC** – Provides the networking environment

## Auto Scaling Configuration

The Auto Scaling Group is configured with:

| Setting | Value |
|---|---:|
| Minimum capacity | 2 |
| Desired capacity | 2 |
| Maximum capacity | 3 |
| Scaling policy | Target Tracking |
| Target CPU utilization | 50% |

When CPU utilization increases, the Auto Scaling Group can launch additional EC2 instances.

When the workload decreases, the ASG can reduce the number of instances while respecting the configured minimum capacity.

## Implementation

### 1. EC2 Setup

Created EC2 instances to host the web application.

The instances are deployed across Availability Zones to improve availability.

### 2. Launch Template

Created a Launch Template containing the configuration required to launch EC2 instances.

The Auto Scaling Group uses this template when launching new instances.

### 3. Target Group

Created a Target Group for the EC2 instances.

The Target Group performs health checks and allows the Application Load Balancer to route traffic only to healthy targets.

### 4. Application Load Balancer

Configured an Application Load Balancer to receive incoming application traffic.

The ALB forwards requests to the Target Group.

### 5. Auto Scaling Group

Created an Auto Scaling Group to manage the EC2 instances.

The ASG maintains the required capacity and automatically launches or terminates instances based on the scaling policy.

### 6. Target Tracking Policy

Configured a Target Tracking scaling policy with a target CPU utilization of **50%**.

```text
CPU utilization increases
          ↓
Target Tracking detects increased load
          ↓
ASG launches additional EC2 instance
          ↓
ALB distributes traffic across healthy instances
