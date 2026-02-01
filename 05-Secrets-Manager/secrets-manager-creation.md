# AWS Secrets Manager Fundamentals

**Lab 5 – AWS Cloud Photo Sharing Application**

## Overview

This lab focuses on **secure credential management** using **AWS Secrets Manager**.
Instead of storing sensitive information such as usernames and passwords directly in code or configuration files, Secrets Manager provides a centralized, encrypted vault that applications can access securely at runtime.

The objective is to eliminate hardcoded secrets and enforce **least-privilege access** through IAM.


## Environment

* AWS Console (lab-provided temporary account)
* AWS CLI / CloudShell
* Region: `us-east-1 (N. Virginia)`


## Service Summary

| Component     | Configuration             |
| ------------- | ------------------------- |
| Service       | AWS Secrets Manager       |
| Secret Name   | `lab/testing/secret`      |
| Secret Type   | Generic (Key-Value pairs) |
| Encryption    | AWS-managed KMS key       |
| Rotation      | Disabled (lab scope)      |
| Access Method | AWS CLI (API-based)       |


## Problem Statement

Hardcoding credentials such as database passwords inside application code introduces serious security risks:

* Secrets leak when code is shared
* Credentials are difficult to rotate
* Access cannot be audited or restricted properly


## Solution Architecture

AWS Secrets Manager solves this by:

* Storing secrets securely in an encrypted vault
* Allowing access **only through IAM-authorized API calls**
* Enabling applications to retrieve secrets dynamically at runtime
* Providing auditing via AWS CloudTrail


## Task 1: Create a Generic Secret

A generic secret was created to store credentials as key-value pairs.

### Configuration Details

| Key      | Value          |
| -------- | -------------- |
| username | `student`      |
| password | `Password123!` |

### Secret Properties

* Secret name: `lab/testing/secret`
* Encryption key: Default AWS-managed KMS key
* Automatic rotation: Disabled

### Key Observations

* Secrets are encrypted immediately upon creation
* The secret value is never exposed unless explicitly retrieved
* Secret names can follow hierarchical naming patterns for organization

## Task 2: Retrieve Secret via AWS CLI

The secret was retrieved programmatically using the AWS CLI to simulate real-world application access.

### Command Used

```bash
aws secretsmanager get-secret-value \
  --secret-id lab/testing/secret \
  --region us-east-1
```

### Result

* The command returned a JSON response
* The `SecretString` field contained the stored credentials
* This confirms successful API-based access

### Why This Matters

This is the same mechanism used by:

* Backend applications
* Lambda functions
* CI/CD pipelines

No credentials are stored in code — they are fetched **only when needed**.

---

## Security Model

### IAM-Based Access Control

* Secrets Manager does **not** allow access by default
* Explicit IAM permissions are required:

  * `secretsmanager:GetSecretValue`
  * `secretsmanager:DescribeSecret`

### Encryption Enforcement

* Secrets are encrypted at rest using KMS
* Decryption only occurs after IAM authorization
* Unauthorized users cannot read secrets — even if they access the AWS account

## Verification Checklist

The following checks were completed:

* Secret `lab/testing/secret` exists
* Secret contains `username` and `password` keys
* Secret retrieval via CLI succeeds
* Access control enforced through IAM
* Encryption enabled by default

## Key Observations

* Hardcoded credentials are completely eliminated
* Secrets are retrieved dynamically at runtime
* IAM acts as the first security gate
* KMS encryption protects secrets at rest
* This pattern aligns with production security best practices


## Screenshots Include

* Secret creation screen
* Key-value configuration
* Secret details page
* CLI output showing `SecretString`
* Region and service verification



## Conclusion

This lab implemented a **production-grade secret management pattern** by:

* Centralizing credentials securely
* Enforcing IAM-based access control
* Removing secrets from application code entirely

This approach is critical for building **secure, auditable, and scalable cloud applications** and is a standard requirement in real-world AWS environments.