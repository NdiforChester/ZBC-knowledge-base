# AWS Storage and Database Services

AWS provides managed storage and database services for storing, protecting, scaling, and analyzing application data. Choosing the right service depends on the kind of data, how the application accesses it, durability needs, performance expectations, and cost.

This guide takes a beginner from basic storage concepts to practical intermediate AWS service selection.

## 1. What Is Cloud Storage?

Cloud storage stores data on remote infrastructure that users and applications access over a network, usually through APIs, protocols, or managed service integrations.

Benefits of cloud storage include:

- Scalability
- High availability
- Cost efficiency
- Durability
- Security controls
- Backup and disaster recovery
- Global accessibility

## 2. Amazon S3

Amazon Simple Storage Service (Amazon S3) is object storage for storing and retrieving data at any scale.

Common use cases include:

- Static website assets
- Backup and recovery
- Data lakes
- Media storage
- Application logs
- Static file storage

### Key Concepts

#### Buckets

A bucket is a container for objects in Amazon S3.

Example bucket name:

```text
my-company-backups
```

#### Objects

Objects are the files or data units stored in S3. Each object includes:

- Data
- Metadata
- A unique key

#### Object Keys

An object key is the unique name used to identify an object inside a bucket.

Example object key:

```text
images/profile.png
```

### Storage Classes

S3 provides storage classes for different access patterns and cost requirements.

| Storage class | Common use case |
| --- | --- |
| S3 Standard | Frequently accessed data |
| S3 Intelligent-Tiering | Data with changing or unknown access patterns |
| S3 Standard-IA | Infrequently accessed data |
| S3 One Zone-IA | Infrequently accessed data stored in one Availability Zone |
| S3 Glacier Instant Retrieval | Archived data that needs millisecond retrieval |
| S3 Glacier Flexible Retrieval | Long-term archive data |
| S3 Glacier Deep Archive | Lowest-cost long-term archive data |

### Features

#### Versioning

Versioning keeps multiple versions of an object. It helps recover deleted files and protect against accidental overwrites.

#### Lifecycle Policies

Lifecycle policies automatically transition or expire objects.

Examples:

- Move files to S3 Glacier after 90 days.
- Delete logs after 1 year.

#### Cross-Region Replication

Cross-Region Replication (CRR) automatically copies objects to another AWS Region.

#### Server-Side Encryption

Server-side encryption protects data stored in S3.

Common options include:

- SSE-S3
- SSE-KMS
- SSE-C

#### Static Website Hosting

S3 can host static websites made of HTML, CSS, JavaScript, images, and other static assets.

### Security Best Practices

- Block public access unless public access is required.
- Use IAM policies and bucket policies carefully.
- Enable encryption.
- Enable versioning for important buckets.
- Enable logging and monitoring.
- Use MFA Delete for critical buckets when appropriate.

## 3. Amazon EBS

Amazon Elastic Block Store (Amazon EBS) provides block storage volumes for Amazon EC2 instances. EBS volumes are commonly used as virtual disks for operating systems, databases, and applications that require low-latency block storage.

### Key Features

- Persistent storage
- High performance
- Snapshots for backup
- Encryption support
- Scalable capacity and performance

### Volume Types

| Volume type | Description |
| --- | --- |
| gp3 and gp2 | General Purpose SSD |
| io2 and io1 | Provisioned IOPS SSD for high-performance workloads |
| st1 | Throughput Optimized HDD |
| sc1 | Cold HDD |

### Snapshots

EBS snapshots are point-in-time backups stored in Amazon S3-managed infrastructure.

Benefits include:

- Disaster recovery
- Backup and restore
- Volume migration across Availability Zones or Regions

### EBS vs. S3

| Feature | EBS | S3 |
| --- | --- | --- |
| Storage type | Block | Object |
| Commonly used with | EC2 instances | Applications, users, and AWS services through APIs |
| Access model | Usually attached to one EC2 instance; selected io1/io2 volumes support Multi-Attach in one Availability Zone | Internet/API access, subject to permissions |
| Performance profile | Low-latency block I/O | Highly scalable object storage |

## 4. Amazon EFS

Amazon Elastic File System (Amazon EFS) provides scalable file storage for Linux-based workloads.

EFS supports multiple compute resources accessing the same file system at the same time.

### Features

- Fully managed file storage
- Elastic scaling
- Shared file access
- High availability
- NFS protocol support

### Common Use Cases

- Web servers
- Content management systems
- Shared application storage
- Analytics workloads

### EFS vs. EBS

| Feature | EFS | EBS |
| --- | --- | --- |
| Storage type | File | Block |
| Shared access | Yes | Usually no; Multi-Attach has specific io1/io2 requirements |
| Scaling | Automatic | Manual capacity and performance choices |
| Best for | Shared Linux workloads | Single-instance block storage workloads |

## 5. Amazon FSx

Amazon FSx provides fully managed file systems for specialized workloads.

| FSx service | Best use case |
| --- | --- |
| FSx for Windows File Server | Windows applications and SMB file shares |
| FSx for Lustre | High-performance computing and machine learning |
| FSx for NetApp ONTAP | Enterprise workloads using NetApp features |
| FSx for OpenZFS | Linux workloads requiring OpenZFS features |

## 6. AWS Storage Gateway

AWS Storage Gateway connects on-premises environments with AWS cloud storage.

| Gateway type | Purpose |
| --- | --- |
| File Gateway | File-based cloud storage access |
| Volume Gateway | Block storage backed by AWS |
| Tape Gateway | Virtual tape backups |

## 7. AWS Backup

AWS Backup provides centralized backup management for supported AWS services.

Supported services include:

- EC2
- EBS
- RDS
- DynamoDB
- EFS
- FSx

Benefits include:

- Centralized backup management
- Automated backups
- Compliance support
- Backup monitoring

## 8. AWS Database Services

### What Is a Database?

A database is an organized collection of data that can be stored, managed, queried, and retrieved efficiently.

### Types of Databases in AWS

| Database type | AWS service example |
| --- | --- |
| Relational database | Amazon RDS |
| MySQL/PostgreSQL-compatible relational database | Amazon Aurora |
| NoSQL database | Amazon DynamoDB |
| Data warehouse | Amazon Redshift |
| In-memory database | Amazon ElastiCache |

## 9. Amazon RDS

Amazon Relational Database Service (RDS) manages relational databases such as PostgreSQL, MySQL, MariaDB, Oracle, and SQL Server.

RDS helps with:

- Automated backups.
- Patching.
- Multi-AZ high availability.
- Read replicas.
- Monitoring.

Use RDS when your application needs structured relational data, SQL queries, transactions, and mature database engines.

## 10. Amazon Aurora

Amazon Aurora is a MySQL-compatible and PostgreSQL-compatible relational database built for AWS. It is designed for higher availability and performance than many self-managed database setups.

Use Aurora for production relational workloads that need strong scaling and availability features.

## 11. Amazon DynamoDB

DynamoDB is a fully managed NoSQL key-value and document database.

Use DynamoDB when you need:

- Very low latency.
- Automatic scaling.
- Serverless operation.
- High request volume.
- Simple key-based access patterns.

Design matters in DynamoDB. You should understand your access patterns before creating tables and indexes.

## 12. Amazon Redshift

Amazon Redshift is a cloud data warehouse used for analytics and reporting across large datasets.

Use Redshift for analytical queries, dashboards, and business intelligence workloads. Do not use it as a normal application transaction database.

## 13. How to Choose Storage

| Need | Common AWS choice |
| --- | --- |
| Store images, backups, logs, or static files | S3 |
| Attach a disk to one EC2 instance | EBS |
| Share Linux files across multiple instances | EFS |
| Windows shared file storage | FSx for Windows File Server |
| Centralized backups | AWS Backup |
| Relational application database | RDS or Aurora |
| Serverless key-value database | DynamoDB |
| Analytics warehouse | Redshift |

## 14. Beginner to Intermediate Practice Path

1. Create an S3 bucket in a lab account.
2. Upload and organize objects with prefixes.
3. Enable S3 versioning.
4. Write a lifecycle rule.
5. Attach an EBS volume to an EC2 instance.
6. Compare EBS, EFS, and S3.
7. Create a small RDS database.
8. Explain when DynamoDB is better than RDS.

## 15. Common Mistakes to Avoid

- Making S3 buckets public without a real requirement.
- Using EBS when object storage would be simpler and cheaper.
- Forgetting backups for databases.
- Choosing DynamoDB before understanding access patterns.
- Storing secrets inside object files or application code.
- Ignoring lifecycle policies for old logs and backups.
