
# Amazon S3 – Object Storage Fundamentals

**Lab 6 – AWS Cloud Photo Sharing Application**

---

## Overview

This lab introduces **Amazon Simple Storage Service (S3)** as the primary object storage layer for the photo-sharing application.

The objective is to create a **secure, encrypted S3 bucket**, upload and manage objects, optimize storage costs using storage classes, and access data programmatically using the AWS CLI—mirroring real-world production workflows.

---

## Environment

* AWS Console (lab-provided temporary account)
* Region: `us-east-1 (N. Virginia)`
* AWS CLI (lab machine / CloudShell)

---

## Storage Design Summary

| Component            | Configuration                                  |
| -------------------- | ---------------------------------------------- |
| S3 Bucket            | `kodekloud-lab-bucket-<unique-name>`            |
| Public Access        | Blocked (All)                                  |
| Default Encryption   | SSE-S3 (Amazon S3 managed keys)                |
| Object Storage Class | Standard → Standard-IA                         |
| Access Method        | AWS Console + AWS CLI                          |

---

## Bucket Configuration

A new S3 bucket was created to store application objects securely.

### Key Configuration Decisions

* **Globally unique bucket name** to meet S3 naming requirements
* **ACLs disabled** to enforce IAM-based access control
* **Block all public access** enabled to prevent accidental exposure
* **Server-side encryption (SSE-S3)** enabled by default
* **Bucket Key enabled** to reduce KMS-related encryption costs

This configuration ensures that all data is private and encrypted at rest by default.

---

## Object Management

### Uploading Objects

A sample file was uploaded to the bucket to simulate application data storage.

* Objects are stored as immutable blobs
* Metadata and storage class are managed independently of the bucket

### Storage Class Optimization

The uploaded object’s storage class was changed:

* **From:** Standard  
* **To:** Standard-IA (Infrequent Access)

This demonstrates how storage costs can be optimized for data that is not accessed frequently but must remain immediately available.

---

## Programmatic Access (AWS CLI)

To simulate real application behavior, the AWS CLI was used to interact with S3.

### List Bucket Contents

```bash
aws s3 ls s3://<bucket-name>/ --region us-east-1
````

### Download an Object

```bash
aws s3 cp s3://<bucket-name>/<file-name> /root/downloaded-file.txt --region us-east-1
```

This workflow reflects how:

* Applications
* Automation scripts
* CI/CD pipelines

interact with S3 without relying on the AWS Console.

---

## Security Considerations

* Objects are encrypted **at rest** using SSE-S3
* Access is governed entirely by **IAM permissions**
* Public access is blocked at the bucket level
* Storage classes do not affect encryption or access control

S3 integrates natively with IAM, CloudTrail, and KMS, making it suitable for highly regulated workloads.

---

## Verification Checklist

The following checks were completed:

* S3 bucket exists with public access blocked
* Default encryption is enabled using SSE-S3
* Object uploaded successfully
* Object storage class updated to Standard-IA
* File downloaded successfully using AWS CLI

---

## Key Observations

* S3 buckets are private by default when public access is blocked
* Encryption is transparent to applications
* Storage class changes do not affect object accessibility
* CLI access is essential for automation and production workflows

---

## Screenshots Included

* Bucket creation settings
* Default encryption configuration
* Object upload confirmation
* Storage class modification
* CLI commands and output

---

## Conclusion

This lab established a secure and scalable object storage foundation using Amazon S3.

By combining encryption, access control, cost optimization, and programmatic access, S3 becomes a core building block for:

* Application assets
* User-uploaded media
* Backups and logs
* Data pipelines

This storage layer will be used extensively in the **Photo Sharing App capstone**, particularly for image uploads, retrieval, and integration with Lambda and CloudFront.

