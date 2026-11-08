# AWS Real-Time Infrastructure Monitoring

## Project Overview

This project demonstrates the deployment and monitoring of a Linux-based cloud server using Amazon Web Services (AWS).

The objective is to implement a practical infrastructure monitoring solution that detects abnormal server activity, generates CloudWatch alarms, and delivers automated email notifications using Amazon SNS.

## Architecture

**AWS Services**
- Amazon EC2 – Linux virtual server
- Amazon VPC – Network infrastructure
- AWS IAM – Identity and access management
- Amazon CloudWatch – Metrics, dashboards and alarms
- Amazon SNS – Automated email notifications
- AWS Systems Manager – Secure server management

## Key Features

- Cloud infrastructure deployment
- Real-time CPU monitoring
- Memory utilization monitoring
- Automated CloudWatch alarms
- Email notifications through SNS
- Incident simulation and troubleshooting
- Infrastructure cost management

## Project Implementation

1. AWS account preparation
2. VPC and networking configuration
3. EC2 Linux instance deployment
4. CloudWatch monitoring configuration
5. SNS notification integration
6. Incident simulation and troubleshooting
7. Testing and verification
8. Documentation and cost cleanup

## Security Considerations

- Apply least-privilege IAM permissions.
- Avoid exposing SSH to the entire internet.
- Never commit AWS credentials or secrets.
- Use secure server management practices.

## Cost Management

Resources will be monitored for AWS charges and deleted when no longer required.

## Project Status

In progress – infrastructure deployment and monitoring configuration.

## Author

Cloud Engineering Portfolio Project
