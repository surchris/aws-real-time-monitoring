# EC2 Linux Server Configuration

## Instance Details

- Instance Name: ec2-monitoring-linux-01
- Instance Type: t3.micro
- Operating System: Amazon Linux 2023
- Storage: 8 GiB gp3
- Region: ap-south-1 (Mumbai)

## Networking

- VPC: vpc-monitoring-project
- Subnet: subnet-monitoring-public
- Security Group: gg-monitoring-ec2
- Public IP: Dynamically assigned

## Security

- IAM Role: role-ec2-monitoring-project
- Systems Manager: Session Manager
- SSH inbound access: Disabled
- Security Group: No inbound rules

## Purpose

This EC2 instance provides the Linux infrastructure for the AWS real-time monitoring project.

CloudWatch monitoring and automated incident notifications will be configured in subsequent phases.

## Deployment Status

Update after successful deployment and verification.
