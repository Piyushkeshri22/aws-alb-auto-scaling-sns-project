# Application Load Balancer Configuration

## Overview

An Application Load Balancer (ALB) was configured to distribute incoming application traffic across healthy EC2 instances managed by the Auto Scaling Group.

## Traffic Flow

```text
User
  |
  v
Application Load Balancer
  |
  v
Target Group
  |
  +----> EC2 Instance 1
  |
  +----> EC2 Instance 2
  |
  +----> Additional EC2 Instance
