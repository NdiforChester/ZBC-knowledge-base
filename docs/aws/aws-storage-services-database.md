# AWS Storage and Database Practice Guide

This guide supports the main [AWS Storage and Database Services](aws-storage-services.md) notes. It focuses on service selection, practical scenarios, and beginner-to-intermediate review exercises.

## 1. Storage Service Selection

AWS has different storage services because applications store data in different ways.

| Requirement | Recommended service | Why |
| --- | --- | --- |
| Store images, videos, backups, logs, or static files | Amazon S3 | Durable object storage accessed through APIs |
| Attach a disk to one EC2 instance | Amazon EBS | Low-latency block storage |
| Share files across multiple Linux instances | Amazon EFS | Managed shared file storage |
| Run Windows file shares | Amazon FSx for Windows File Server | Managed SMB file system |
| Store high-performance machine learning or HPC files | Amazon FSx for Lustre | High-throughput file system |
| Centralize backups across AWS services | AWS Backup | Managed backup policies and monitoring |

## 2. Database Service Selection

Choose the database based on access pattern, data structure, scaling needs, and operational model.

| Requirement | Recommended service | Why |
| --- | --- | --- |
| SQL database for a web application | Amazon RDS | Managed relational database engines |
| High-performance MySQL or PostgreSQL-compatible database | Amazon Aurora | AWS-optimized relational database |
| Key-value or document database at high scale | Amazon DynamoDB | Fully managed NoSQL database |
| Analytics and reporting across large datasets | Amazon Redshift | Data warehouse for analytical queries |
| Cache frequent reads or session data | Amazon ElastiCache | In-memory low-latency access |

## 3. Scenario Examples

### Scenario 1: User Profile Photos

Use Amazon S3.

Reason:

- Photos are objects.
- S3 scales without managing disks.
- Lifecycle policies can move old files to cheaper storage.
- CloudFront can improve delivery speed.

### Scenario 2: Database for an Online Store

Use Amazon RDS or Amazon Aurora.

Reason:

- Orders, customers, payments, and inventory usually need relational data.
- SQL queries and transactions are useful.
- Multi-AZ deployment can improve availability.

### Scenario 3: Shared Web Content Across Servers

Use Amazon EFS.

Reason:

- Multiple Linux servers can mount the same file system.
- Capacity grows automatically.
- It supports shared application content.

### Scenario 4: Fast Session Lookup

Use Amazon ElastiCache.

Reason:

- Session data is read frequently.
- In-memory access is faster than repeated database queries.
- It can reduce database load.

### Scenario 5: Application Event Data at High Scale

Use Amazon DynamoDB.

Reason:

- It supports high request volume.
- It can scale without managing database servers.
- It works well when access patterns are known in advance.

## 4. Security Checklist

Use this checklist when reviewing AWS storage and database designs:

- Is public access blocked unless explicitly required?
- Is encryption enabled?
- Are IAM permissions limited to least privilege?
- Are database subnets private?
- Are security groups restricted?
- Are backups enabled?
- Are logs and metrics monitored?
- Are old objects managed with lifecycle rules?
- Are secrets stored outside source code?

## 5. Backup and Recovery Checklist

For production systems, define:

- Recovery Point Objective (RPO): how much data loss is acceptable.
- Recovery Time Objective (RTO): how quickly the system must recover.
- Backup frequency.
- Backup retention period.
- Restore testing schedule.
- Cross-Region backup requirement.

Backups are only useful if the team knows how to restore them.

## 6. Cost Awareness

Storage and database costs can grow quietly.

Cost controls:

- Use S3 lifecycle policies.
- Delete unused EBS volumes.
- Remove old snapshots that are no longer needed.
- Right-size RDS instances.
- Use DynamoDB on-demand or provisioned capacity based on traffic patterns.
- Monitor usage with AWS Budgets and Cost Explorer.

## 7. Practice Questions

1. When should you choose S3 instead of EBS?
2. Why should production RDS databases usually be private?
3. What is the difference between object storage and block storage?
4. Why is DynamoDB data modeling based on access patterns?
5. How do lifecycle policies reduce S3 cost?
6. What is the difference between backup retention and point-in-time recovery?
7. Why should teams test restore procedures?

## 8. Lab Ideas

1. Create an S3 bucket and upload test files.
2. Enable S3 versioning and delete a file, then restore it.
3. Create a lifecycle rule for old objects.
4. Attach an EBS volume to a lab EC2 instance.
5. Create an RDS database in a private subnet in a lab environment.
6. Create a DynamoDB table and query by partition key.
7. Create a CloudWatch alarm for a database metric.

## 9. Common Mistakes to Avoid

- Using one storage service for every problem.
- Exposing databases publicly.
- Forgetting to enable backups.
- Keeping unused snapshots forever.
- Using DynamoDB without understanding query patterns.
- Storing access keys or passwords in documentation examples.
