# Troubleshooting and Lessons Learned

This project involved troubleshooting AWS infrastructure and application issues during implementation.

## 1. EC2 Instance Health

### Problem

An EC2 instance initially showed an initializing or unhealthy status.

### Troubleshooting

Checked:

- EC2 instance status checks
- Instance state
- Security Group configuration
- Application availability

### Resolution

Verified the instance status checks and application availability before using the instance as an application target.

---

## 2. Target Group Health

### Problem

The Target Group must contain healthy targets before the Application Load Balancer can successfully route traffic.

### Troubleshooting

Checked:

- Target registration
- Health check status
- EC2 instance state
- Security Group rules
- Application port

### Resolution

Verified the application and networking configuration so that Target Group health checks could reach the application.

---

## 3. Auto Scaling Behavior

### Problem

The number of EC2 instances changes according to the configured scaling policy and workload.

### Troubleshooting

Checked:

- Desired capacity
- Minimum capacity
- Maximum capacity
- Target Tracking policy
- CPU utilization
- CloudWatch alarms

### Configuration

```text
Minimum capacity: 2
Desired capacity: 2
Maximum capacity: 3
Target CPU utilization: 50%
```

### Resolution

Verified that the Auto Scaling Group and Target Tracking policy were configured with the intended capacity limits and CPU target.

---

## 4. CloudWatch Alarm States

### Problem

CloudWatch alarms can show different states depending on the current metric values.

### Troubleshooting

Checked:

- CPUUtilization metric
- Alarm state
- Alarm actions
- Auto Scaling policy
- Instance metrics

### Resolution

Verified the alarm configuration and its relationship with the Auto Scaling setup.

---

## 5. SNS Email Notification

### Problem

SNS email subscriptions require confirmation before notifications can be delivered.

### Troubleshooting

Checked:

- SNS topic
- Email subscription
- Subscription confirmation
- Notification configuration

### Resolution

Confirmed the email subscription and verified the SNS notification configuration.

---

## Key Lessons

The project helped me understand how AWS services work together:

```text
ALB
 |
 v
Target Group
 |
 v
EC2 Instances
 |
 v
Auto Scaling Group
 |
 v
CloudWatch
 |
 v
SNS
 |
 v
Email Notification
```

Troubleshooting also reinforced the importance of checking application health, networking, monitoring metrics, and service dependencies when diagnosing AWS infrastructure.
