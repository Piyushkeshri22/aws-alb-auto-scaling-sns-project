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
```

## Target Group

The Target Group registers EC2 instances and performs health checks to determine which targets are healthy.

![Target Group](../screenshots/03-target-group.png)

## Application Load Balancer

The ALB receives incoming application requests and forwards them to the Target Group.

![Application Load Balancer](../screenshots/04-application-load-balancer.png)

## Integration with Auto Scaling

The Target Group is associated with the Auto Scaling Group. As the ASG changes capacity, targets can be registered or deregistered from the load-balancing path.

## Related Components

- Application Load Balancer
- Target Group
- EC2 Instances
- Auto Scaling Group
- Health Checks
