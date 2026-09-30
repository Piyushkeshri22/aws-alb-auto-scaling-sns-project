# Amazon SNS Configuration

## Overview

Amazon Simple Notification Service (SNS) was configured to send email notifications for monitoring events in this project.

SNS provides a notification mechanism so that important infrastructure events can be communicated through email.

## SNS Notification Flow

```text
CloudWatch
    |
    v
Alarm / Monitoring Event
    |
    v
Amazon SNS Topic
    |
    v
Email Subscription
    |
    v
Email Notification
