# AWS Real-Time Infrastructure Monitoring & Automated Alerting

## Project Overview

Designed and implemented an AWS cloud infrastructure monitoring solution to track Linux server performance, detect resource utilization issues, and generate automated email notifications.

The project demonstrates practical AWS Cloud Engineering skills in infrastructure provisioning, Linux administration, monitoring, incident detection, troubleshooting, and cost management.

**Project Status:** Infrastructure deployment, monitoring, and alerting completed. Portfolio documentation in progress.

## AWS Services and Technologies

- **Amazon VPC:** Network infrastructure and subnet configuration
- **Amazon EC2:** Amazon Linux 2023 monitoring server
- **AWS IAM / IAM Identity Center:** Access management
- **Amazon CloudWatch:** Metrics, dashboards, and alarms
- **Amazon CloudWatch Agent:** Memory and disk metric collection
- **Amazon SNS:** Automated email notifications
- **AWS Systems Manager:** Included in the project architecture for secure server management
- **Linux:** Server administration and troubleshooting
- **GitHub:** Project documentation and version control

## Architecture

The monitoring workflow is:

AWS VPC
  |
  +-- EC2 Instance (Amazon Linux 2023)
        |
        +-- EC2 CPU and Health Metrics
        |
        +-- CloudWatch Agent
              |
              +-- Memory Utilization
              +-- Disk Utilization
                    |
              Amazon CloudWatch
                    |
              CloudWatch Alarms
                    |
              Amazon SNS Topic
                    |
              Email Notification
```

## Key Features

- AWS VPC and EC2 infrastructure deployment
- Linux server configuration and verification
- CPU, memory, and disk utilization monitoring
- CloudWatch dashboard with performance graphs
- Automated threshold-based CloudWatch alarms
- SNS email notification integration
- Controlled alarm-state testing
- Alarm history verification
- Infrastructure cost management

## Monitoring Configuration

| Metric | Threshold | Evaluation |
|---|---|---|
| CPU Utilization | >70% | 5 out of 5 one-minute datapoints |
| Memory Utilization | >80% | 5 out of 5 one-minute datapoints |
| Disk Utilization | >85% | 5 out of 5 one-minute datapoints |

CloudWatch Agent publishes memory and disk utilization metrics to the `CWAgent` namespace.

CPU utilization is monitored using the native `AWS/EC2` namespace.

## Implementation

### Phase 1 — Infrastructure Deployment

1. Configured AWS access using IAM Identity Center.
2. Created and verified VPC networking resources.
3. Configured EC2 security group rules.
4. Launched an Amazon Linux 2023 EC2 instance.
5. Verified instance health and Linux connectivity.

### Phase 2 — Infrastructure Monitoring

1. Installed the Amazon CloudWatch Agent.
2. Configured memory and disk metric collection.
3. Verified CloudWatch Agent service status.
4. Created the EC2 monitoring dashboard.
5. Verified CPU, memory, disk, and instance health monitoring.

### Phase 3 — Automated Alerting

1. Created the SNS topic `EC2-Monitoring-Alerts`.
2. Configured and confirmed an email subscription.
3. Created the CPU utilization alarm.
4. Created the memory utilization alarm.
5. Created the disk utilization alarm.
6. Verified all three alarms reached the OK state.
7. Published a successful SNS test message.
8. Performed a controlled CloudWatch alarm-state test.
9. Received the CloudWatch ALARM notification.
10. Verified successful SNS action history and return to OK.

## Testing and Validation

| Test | Result |
|---|---|
| EC2 instance health checks | Passed |
| CloudWatch Agent service | Passed |
| CPU metric visualization | Passed |
| Memory metric visualization | Passed |
| Disk metric visualization | Passed |
| CPU alarm | Passed |
| Memory alarm | Passed |
| Disk alarm | Passed |
| SNS test message delivery | Passed |
| CloudWatch-to-SNS notification | Passed |
| Alarm recovery to OK | Passed |

**Note:** The controlled alarm test verified notification integration without generating artificial CPU, memory, or disk load.

## Security Considerations

- Follow least-privilege IAM practices.
- Avoid exposing SSH access to unrestricted networks.
- Never commit AWS credentials, access keys, or secrets.
- Use secure administrative access methods.
- Review security groups and resource permissions.

## Cost Management

- Stop EC2 instances when not required.
- Review EBS storage and snapshot charges.
- Monitor CloudWatch custom metric and alarm charges.
- Review SNS usage.
- Delete unused resources after preserving required project documentation.

Stopping an EC2 instance does not eliminate every AWS charge.

## Future Improvements

- Provision infrastructure using Terraform.
- Automate deployment using GitHub Actions or Jenkins.
- Implement Ansible for server configuration.
- Add CloudWatch Logs monitoring.
- Implement automated incident remediation.
- Expand monitoring to multiple EC2 instances.

## Project Author

AWS Cloud Engineering Portfolio Project

**Repository:** https://github.com/surchris/aws-real-time-monitoring
