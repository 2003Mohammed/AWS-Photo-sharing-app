---

# AWS Photo Sharing App – Hands-On Labs

**About**
Hands-on AWS course to build a production-ready, Instagram-like Photo Sharing App. Learn core AWS services—VPC, IAM, KMS, RDS, Secrets Manager, S3, Lambda, ALB, EC2, CloudWatch—and integrate them into a secure, scalable, serverless 3-tier application with real-time monitoring and image processing.

---

## Repository Overview

This repository documents a step-by-step, hands-on approach to building a complete cloud application on AWS. Each lab focuses on a core service, and the final **capstone project** integrates all services into a functional photo-sharing platform.

**Core Services Covered:**

* **Networking:** VPC, Subnets, Internet Gateway, Route Tables
* **Security & Identity:** IAM Users, Groups, Roles; KMS; Secrets Manager
* **Compute:** EC2, Lambda, Application Load Balancer
* **Storage:** RDS (Relational Database Service), S3
* **Monitoring:** CloudWatch dashboards, alarms

---

## Labs Included

| Lab                    | Description                                                      | Folder           |
| ---------------------- | ---------------------------------------------------------------- | ---------------- |
| Lab 1: VPC             | Build secure networks with public/private subnets and IGW        | `01-vpc/`        |
| Lab 2: IAM             | Create users, groups, and roles with least-privilege access      | `02-iam/`        |
| Lab 3: KMS             | Configure encryption for sensitive data                          | `03-kms/`        |
| Lab 4: RDS             | Deploy a relational database with multi-AZ setup                 | `04-rds/`        |
| Lab 5: Secrets Manager | Securely store and retrieve secrets                              | `05-secrets/`    |
| Lab 6: S3              | Object storage with pre-signed URLs                              | `06-s3/`         |
| Lab 7: ALB             | Set up traffic distribution for web tier                         | `07-alb/`        |
| Lab 8: Lambda          | Create serverless functions for image processing                 | `08-lambda/`     |
| Lab 9: EC2             | Launch Docker-based application instances                        | `09-ec2/`        |
| Lab 10: CloudWatch     | Monitor and set alarms for infrastructure                        | `10-cloudwatch/` |
| Lab 11: Capstone       | Integrate all services into a fully functional photo-sharing app | `11-capstone/`   |

---

## Skills Demonstrated

* Designing secure, isolated AWS networks
* Managing identity and permissions with IAM
* Implementing encryption and secrets management
* Deploying databases and storage solutions
* Building serverless workflows and scalable compute
* Monitoring, logging, and alerting for production-ready applications
* Integrating multiple AWS services into a cohesive application

---

## Repository Structure

```
aws-photo-sharing-app-learning/
├── README.md
├── architecture/
│   ├── high-level-architecture.md
│   └── diagrams.png
├── 01-vpc/
├── 02-iam/
├── 03-kms/
├── 04-rds/
├── 05-secrets/
├── 06-s3/
├── 07-alb/
├── 08-lambda/
├── 09-ec2/
├── 10-cloudwatch/
└── 11-capstone/
```

---

## How to Use This Repository

1. Explore individual lab folders to see step-by-step documentation and screenshots.
2. Review `architecture/` for high-level design and diagrams of the photo-sharing app.
3. Use the Capstone lab as a reference for **integrating all services** into a production-ready AWS application.

---
