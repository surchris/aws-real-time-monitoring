# AWS EC2 Monitoring Architecture

  AWS["AWS Region: ap-south-1"]
     VPC["Amazon VPC"]
      EC2["EC2: Amazon Linux 2023"]
      Agent["CloudWatch Agent"]
      EC2 --> Agent
    end
    Metrics["Amazon CloudWatch Metrics"]
    Dashboard["Monitoring Dashboard"]
    CPU["CPU Alarm > 70%"]
    MEM["Memory Alarm > 80%"]
    DISK["Disk Alarm > 85%"]
    SNS["SNS: EC2-Monitoring-Alerts"]
    EC2 -->|CPU and status metrics| Metrics
    Agent -->|Memory and disk metrics| Metrics
    Metrics --> Dashboard
    Metrics --> CPU
    Metrics --> MEM
    Metrics --> DISK
    CPU --> SNS
    MEM --> SNS
    DISK --> SNS
  end
  SNS --> Email["Confirmed Email Subscription"]
