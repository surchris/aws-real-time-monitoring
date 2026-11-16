# AWS Cost Management and Cleanup

## Objective
Minimize unnecessary AWS charges while
preserving project documentation.

## Resource Cleanup Checklist

- [ ] Verify EC2 instance state
- [ ] Review EBS volumes and snapshots
- [ ] Check public IPv4 addresses
- [ ] Check for NAT Gateways
- [ ] Review CloudWatch alarms and dashboard
- [ ] Review SNS topics and subscriptions
- [ ] Review AWS Cost Explorer
- [ ] Verify GitHub backups and documentation

## Resource Preservation

Preserve:
- CloudWatch Agent configuration
- AWS architecture diagram
- Monitoring screenshots
- SNS notification evidence
- Testing and validation documentation

## Important Notes

Stopping EC2 generally stops compute charges,
but EBS storage and other resources may
continue to incur charges.

CloudWatch Agent metrics stop publishing
while EC2 is stopped.

## Final Verification

Update checklist items after verifying
actual AWS resources.
