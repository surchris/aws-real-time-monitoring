# AWS EC2 Monitoring — Testing and Validation

## 1. Testing Objective

Validate the successful deployment and operation of an AWS EC2 infrastructure monitoring solution using Amazon CloudWatch, CloudWatch Agent, CloudWatch Alarms, and Amazon SNS.

Testing covered infrastructure availability, metric collection, threshold-based alerting, email notification delivery, and alarm recovery.

**AWS Region:** Asia Pacific (Mumbai) — `ap-south-1`

**EC2 Instance:** `ec2-monitoring-linux-01`

**Operating System:** Amazon Linux 2023

## 2. Infrastructure Validation

| Test ID | Validation | Result |
|---|---|---|
| TC-01 | VPC networking configuration verified | PASS |
| TC-02 | EC2 instance launched successfully | PASS |
| TC-03 | EC2 instance status checks passed | PASS |
| TC-04 | Linux terminal connectivity verified | PASS |
| TC-05 | CloudWatch Agent service running | PASS |

The CloudWatch Agent was verified using:

```bash
sudo systemctl status amazon-cloudwatch-agent --no-pager
```

Observed result:

```text
Active: active (running)
```

## 3. CloudWatch Metrics Validation

| Test ID | Metric | Result |
|---|---|---|
| TC-06 | CPUUtilization | PASS |
| TC-07 | mem_used_percent | PASS |
| TC-08 | disk_used_percent | PASS |
| TC-09 | EC2 health-check metrics | PASS |

The CloudWatch monitoring dashboard displayed CPU, memory, disk utilization, and EC2 health-check metrics.

Memory and disk metrics were collected using the Amazon CloudWatch Agent.

## 4. CloudWatch Alarm Validation

Three utilization alarms were configured.

| Alarm | Threshold | Evaluation | Result |
|---|---|---|---|
| EC2-High-CPU-Alarm | Greater than 70% | 5/5 one-minute datapoints | PASS |
| EC2-High-Memory-Alarm | Greater than 80% | 5/5 one-minute datapoints | PASS |
| EC2-High-Disk-Alarm | Greater than 85% | 5/5 one-minute datapoints | PASS |

All three alarms were verified in the OK state after sufficient metric data was available.

Missing-data handling was configured to treat missing data as missing.

## 5. SNS Notification Testing

**SNS Topic:** `EC2-Monitoring-Alerts`

**Subscription Protocol:** Email

### Test Case TC-10 — SNS Direct Publish

**Procedure:**

1. Opened the Amazon SNS Console.
2. Selected the monitoring SNS topic.
3. Published a test message.
4. Checked the subscribed email inbox.

**Expected Result:** Test message delivered to the subscribed email address.

**Actual Result:** Test email successfully received after a short delay.

**Status:** PASS

### Test Case TC-11 — CloudWatch Alarm Notification

**Procedure:**

1. Opened AWS CloudShell.
2. Used the AWS CLI to set the CPU alarm state to ALARM.
3. Verified receipt of the CloudWatch alarm notification.
4. Reviewed CloudWatch alarm history.

Command used:

```bash
aws cloudwatch set-alarm-state \
  --alarm-name "EC2-High-CPU-Alarm" \
  --state-value ALARM \
  --state-reason "Controlled SNS notification test for AWS Project 1" \
  --region ap-south-1
```

**Expected Result:** CloudWatch executes the configured SNS alarm action and an email notification is received.

**Actual Result:** CloudWatch ALARM email received and SNS action execution verified in alarm history.

**Status:** PASS

This was a controlled alarm-state test. Actual CPU utilization was not deliberately increased above the threshold.

### Test Case TC-12 — Alarm Recovery

**Procedure:**

1. Allowed CloudWatch to resume normal metric evaluation.
2. Refreshed the CloudWatch Alarms console.
3. Verified the CPU alarm returned to OK.

**Actual Result:** CPU alarm returned to OK.

**Status:** PASS

## 6. Final Verification Results

| Component | Validation Status |
|---|---|
| EC2 Infrastructure | PASS |
| CloudWatch Agent | PASS |
| CloudWatch Dashboard | PASS |
| CPU Alarm | PASS |
| Memory Alarm | PASS |
| Disk Alarm | PASS |
| SNS Direct Notification | PASS |
| CloudWatch-to-SNS Notification | PASS |
| CPU Alarm Recovery | PASS |

**Overall Result: PASS**

All planned monitoring and notification integration checks were completed successfully.

## 7. Test Evidence

The repository includes screenshots documenting:

- CloudWatch monitoring dashboard
- CPU, memory, and disk alarm states
- Successful SNS alarm notification

Evidence is stored in the `cloudwatch-monitoring/screenshots/` directory.

Sensitive account information and personal identifiers should be redacted from publicly shared screenshots.

## 8. Testing Limitations

The project validated CloudWatch metric collection and the alarm-to-SNS notification workflow.

The controlled CPU alarm test did not simulate sustained high CPU utilization.

Memory and disk thresholds were verified through configuration and normal-state evaluation, not by deliberately exhausting system resources.

Production deployment would require additional testing of failure scenarios, alarm behavior during outages, permissions, and notification delivery.

## 9. Conclusion

The AWS EC2 infrastructure monitoring solution successfully demonstrated:

- Linux infrastructure monitoring
- CloudWatch metric collection and visualization
- Threshold-based alert configuration
- SNS email notification integration
- Controlled alarm testing
- Monitoring verification and troubleshooting

The implementation provides a practical foundation for cloud operations, incident detection, and automated alerting.
