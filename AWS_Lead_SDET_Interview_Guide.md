# AWS Tricky Interview Questions and Answers for Lead SDET (10+ Years)

## 1. Why does an SDET need AWS knowledge?
Modern applications run in cloud-native environments involving:
- API Gateway
- Lambda
- ECS/EKS
- RDS/DynamoDB
- CloudWatch

Understanding these helps with automation, observability, troubleshooting, and CI/CD integration.

---

## 2. EC2 vs ECS vs EKS

### EC2
- Virtual machines
- Full OS control
- Suitable for legacy applications

### ECS
- AWS-managed container orchestration
- Easier than Kubernetes

### EKS
- Managed Kubernetes
- Best for large-scale containerized environments

---

## 3. Selenium Grid on EC2 is expensive. How would you optimize?
- Move to ECS/EKS
- Use Spot Instances
- Auto-scale execution nodes
- Run browsers headlessly
- Optimize resource allocation

---

## 4. Difference Between S3 and EBS

### S3
- Object storage
- Reports
- Logs
- Screenshots
- Artifacts

### EBS
- Block storage
- Attached to EC2
- Operating system and application files

---

## 5. How would you store automation reports in AWS?
Jenkins
→ Generate Reports
→ Upload to S3
→ Share S3 URL

Benefits:
- Centralized access
- Long-term retention
- Easy sharing

---

## 6. What is AWS Lambda?
Serverless compute service.

Use cases:
- Test data setup
- Environment cleanup
- Trigger automation
- Synthetic monitoring

---

## 7. Lambda vs EC2

| Feature | Lambda | EC2 |
|----------|----------|----------|
| Server Management | No | Yes |
| Scaling | Automatic | Manual |
| Billing | Per execution | Per runtime |
| Long Running Jobs | Limited | Supported |

---

## 8. Explain Auto Scaling
Automatically increases or decreases resources based on metrics.

Example:
CPU > 70%
→ Launch additional instances

---

## 9. What is a Security Group?
Virtual firewall controlling inbound and outbound traffic.

Example:
- Allow 22
- Allow 443
- Block unnecessary ports

---

## 10. Security Group vs NACL

### Security Group
- Instance level
- Stateful

### NACL
- Subnet level
- Stateless

---

## 11. How do you secure secrets?
Use:
- AWS Secrets Manager
- AWS Systems Manager Parameter Store

Avoid:
- Git repositories
- Source code
- Configuration files

---

## 12. What is IAM?
Identity and Access Management.

Principle:
Least Privilege Access

---

## 13. How do you troubleshoot Lambda failures?
Check:
- CloudWatch Logs
- IAM permissions
- Timeout settings
- Memory allocation
- Environment variables

---

## 14. What is CloudWatch?
Monitoring and observability service.

Features:
- Logs
- Metrics
- Alerts
- Dashboards

---

## 15. API tests pass in QA but fail in Production. AWS-related causes?
- Different Security Groups
- Different IAM Roles
- Different Secrets
- Load Balancer differences
- DNS configuration differences

---

## 16. What is a Load Balancer?

### Application Load Balancer (ALB)
- HTTP/HTTPS traffic

### Network Load Balancer (NLB)
- TCP/UDP traffic

---

## 17. Why are health checks important?
Detect unhealthy instances and prevent traffic routing to failed applications.

---

## 18. RDS vs DynamoDB

### RDS
- Relational database
- SQL
- Transactions

### DynamoDB
- NoSQL
- Massive scale
- Low latency

---

## 19. AWS Services for Automation Platform

Typical stack:
- GitHub
- Jenkins
- ECR
- ECS/EKS
- S3
- CloudWatch
- Secrets Manager
- IAM
- RDS

---

## 20. Design a Cloud-Native Automation Platform

GitHub Commit
→ Jenkins Pipeline
→ Build Docker Image
→ Push to ECR
→ Deploy to EKS
→ Run API Automation
→ Run UI Automation
→ Upload Reports to S3
→ Send Metrics to CloudWatch
→ Slack Notifications

### Key Benefits
- Auto-scaling
- Containerized execution
- Secure secret management
- Centralized monitoring
- Cost optimization

---

## Executive-Level Question

### How do you measure AWS automation platform success?

Metrics:
- Reduced execution time
- Lower infrastructure cost
- Improved reliability
- Better scalability
- Faster feedback loops
- Reduced maintenance effort
- Fewer production incidents
