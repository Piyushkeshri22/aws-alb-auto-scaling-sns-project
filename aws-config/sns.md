# Amazon SNS Configuration

## Overview

Amazon Simple Notification Service (SNS) was configured to send email notifications for monitoring events in this project.

## SNS Notification Flow

```text
CloudWatch Alarm
       |
       v
    SNS Topic
       |
       v
Email Subscription
       |
       v
Email Notification
```

## SNS Topic

An SNS topic was created as the notification channel.

![SNS Topic](../screenshots/08-sns-topic.png)

## Email Subscription

An email subscription was configured for the SNS topic.

![SNS Email Notification](../screenshots/09-sns-email-notification.png)

The email subscription must be confirmed before SNS can deliver notifications to the endpoint.

## Integration with CloudWatch

When a CloudWatch alarm is configured with an SNS action, the alarm can publish notifications to the SNS topic when its configured state-change condition occurs.

## Related Services

- Amazon CloudWatch
- Amazon SNS
- Amazon EC2
- Auto Scaling Group
