# Troubleshooting and Lessons Learned

This project involved troubleshooting several AWS infrastructure and application issues during implementation.

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

Waited for the instance status checks to complete and verified that the instance was healthy before using it as an application target.

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

Verified the EC2 application and networking configuration and ensured that the Target Group health checks could reach the application.

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
