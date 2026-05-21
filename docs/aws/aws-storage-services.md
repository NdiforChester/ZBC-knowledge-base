# AWS Storage and Database Services

## Introduction

Amazon Web Services (AWS) provides managed storage and database services for storing, protecting, scaling, and analyzing application data. These services support different access patterns, durability needs, performance requirements, and cost profiles.

This guide covers beginner-to-intermediate AWS storage and database concepts.

## AWS Storage Services

### What Is Cloud Storage?

Cloud storage stores data on remote infrastructure that users and applications access over a network, usually through APIs, protocols, or managed service integrations.

Benefits of cloud storage include:

- Scalability
- High availability
- Cost efficiency
- Durability
- Security controls
- Backup and disaster recovery
- Global accessibility

## Amazon S3

### Overview

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

## Amazon EBS

### Overview

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

## Amazon EFS

### Overview

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

## Amazon FSx

### Overview

Amazon FSx provides fully managed file systems for specialized workloads.

| FSx service | Best use case |
| --- | --- |
| FSx for Windows File Server | Windows applications and SMB file shares |
| FSx for Lustre | High-performance computing and machine learning |
| FSx for NetApp ONTAP | Enterprise workloads using NetApp features |
| FSx for OpenZFS | Linux workloads requiring OpenZFS features |

## AWS Storage Gateway

### Overview

AWS Storage Gateway connects on-premises environments with AWS cloud storage.

| Gateway type | Purpose |
| --- | --- |
| File Gateway | File-based cloud storage access |
| Volume Gateway | Block storage backed by AWS |
| Tape Gateway | Virtual tape backups |

## AWS Backup

### Overview

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

## AWS Database Services

### What Is a Database?

A database is an organized collection of data that can be stored, managed, queried, and retrieved efficiently.

### Types of Databases in AWS

| Database type | AWS service example |
| --- | --- |
| Relational database | Amazon RDS |
| MySQL/PostgreSQL-compatible relational database | Amazon Aurora |
| NoSQL database | Amazon DynamoDB |
| Data warehouse | Amazon Redshift |
| In-memory cache | Amazon ElastiCache |
| Graph database | Amazon Neptune |
| Time-series database | Amazon Timestream |

> Note: Amazon QLDB reached end of support on July 31, 2025. It should not be selected for new learning paths or new workloads. Existing QLDB content should point to AWS migration guidance for Amazon Aurora PostgreSQL.

## Amazon RDS

### Overview

Amazon Relational Database Service (Amazon RDS) is a managed relational database service.

It simplifies:

- Database setup
- Backups
- Patching
- Scaling
- Monitoring

### Supported Database Engines

- MySQL
- PostgreSQL
- MariaDB
- Oracle
- Microsoft SQL Server
- Amazon Aurora

### Features

#### Automated Backups

RDS can automatically back up databases and support point-in-time recovery.

#### Multi-AZ Deployment

Multi-AZ deployments improve availability by maintaining standby database resources in another Availability Zone.

#### Read Replicas

Read replicas improve read scalability for supported engines and workloads.

#### Scaling

RDS supports vertical scaling by changing instance size. Some engines and configurations also support read scaling with replicas.

#### Security

RDS security features include:

- Encryption
- IAM authentication for supported engines
- Security groups
- Network isolation through Amazon VPC

### Use Cases

- Web applications
- ERP systems
- E-commerce platforms
- CRM systems

## Amazon Aurora

### Overview

Amazon Aurora is a high-performance relational database compatible with MySQL and PostgreSQL.

### Key Benefits

- Performance improvements compared with standard MySQL and PostgreSQL deployments
- Automatic storage scaling
- High availability
- Fault tolerance
- Continuous backups

### Architecture

Aurora separates the compute layer from the storage layer. This improves scalability, availability, and resilience.

## Amazon DynamoDB

### Overview

Amazon DynamoDB is a fully managed NoSQL database service.

It provides:

- Low-latency access
- High scalability
- Serverless operation options

### Core Concepts

#### Tables

Tables store related application data.

#### Items

Items are individual records in a table.

#### Attributes

Attributes are data fields within an item.

### Features

#### On-Demand Capacity

On-demand capacity automatically handles variable traffic without capacity planning.

#### Global Tables

Global tables replicate data across Regions for multi-Region applications.

#### DynamoDB Streams

DynamoDB Streams capture item-level changes in a table.

#### TTL

Time to Live (TTL) automatically deletes expired items.

### Use Cases

- Gaming applications
- IoT systems
- Real-time applications
- Shopping carts
- User sessions

## Amazon Redshift

### Overview

Amazon Redshift is a cloud data warehouse service used for analytics, business intelligence, and large-scale reporting.

### Key Features

- Columnar storage
- Parallel query execution
- Integration with BI tools
- Petabyte-scale analytics

### Common Use Cases

- Financial reporting
- Data analytics
- Dashboard reporting
- Big data processing

## Amazon ElastiCache

### Overview

Amazon ElastiCache is an in-memory caching service.

Supported engines include:

- Valkey
- Redis OSS
- Memcached

### Benefits

- Reduces database load
- Improves application response time
- Supports real-time applications

### Common Use Cases

- Session storage
- Gaming leaderboards
- Real-time analytics
- Caching database queries

## Amazon Neptune

### Overview

Amazon Neptune is a graph database service for highly connected datasets.

### Use Cases

- Social networks
- Fraud detection
- Recommendation engines
- Knowledge graphs

## Amazon Timestream

### Overview

Amazon Timestream is a time-series database service.

It is designed for:

- IoT data
- Monitoring systems
- Application metrics

## Database Concepts

### High Availability

High availability helps systems remain operational during failures.

Examples include:

- Multi-AZ deployments
- Replication
- Automated failover

### Scalability

#### Vertical Scaling

Vertical scaling increases resources such as CPU, memory, or storage for a server or database instance.

#### Horizontal Scaling

Horizontal scaling adds more servers, partitions, or replicas.

### Backup and Recovery

Important strategies include:

- Automated backups
- Snapshots
- Point-in-time recovery
- Cross-Region backups

### Database Security Best Practices

- Enable encryption.
- Use IAM roles and least-privilege access.
- Restrict network access with security groups.
- Rotate credentials regularly.
- Enable logging and monitoring.
- Use Multi-Factor Authentication (MFA) for human access to AWS accounts.

## Monitoring AWS Storage and Databases

### Amazon CloudWatch

Amazon CloudWatch provides:

- Metrics
- Logs
- Alarms
- Dashboards

### AWS CloudTrail

AWS CloudTrail records AWS API calls and user activity for auditing and security analysis.

## Service Comparisons

### Storage Service Comparison

| Service | Storage type | Best use case |
| --- | --- | --- |
| S3 | Object | Backup, static content, data lakes, and object storage |
| EBS | Block | EC2 disks and low-latency block storage |
| EFS | File | Shared Linux file systems |
| FSx | File | Specialized enterprise file workloads |

### Database Service Comparison

| Service | Type | Best for |
| --- | --- | --- |
| RDS | Relational | Traditional applications |
| Aurora | Relational | High-performance MySQL/PostgreSQL-compatible applications |
| DynamoDB | NoSQL | Serverless and high-scale applications |
| Redshift | Data warehouse | Analytics |
| ElastiCache | In-memory cache | Caching and low-latency access |
| Neptune | Graph | Connected data |
| Timestream | Time-series | IoT and metrics |

## AWS Shared Responsibility Model

### AWS Is Responsible For

- Physical infrastructure
- Hardware
- Networking infrastructure
- Managed service infrastructure

### Customers Are Responsible For

- Data protection
- IAM permissions
- Application security
- Encryption configuration
- Network access configuration

## Best Practices Summary

### Storage Best Practices

- Choose the correct storage class or service for the access pattern.
- Enable encryption.
- Use lifecycle policies.
- Enable backups.
- Monitor usage and costs.

### Database Best Practices

- Use Multi-AZ deployments for production relational databases when high availability is required.
- Enable automated backups.
- Monitor performance.
- Use least-privilege access.
- Implement disaster recovery plans.

## Conclusion

AWS provides storage and database services for many workload types, including object storage, block storage, shared file systems, relational databases, NoSQL databases, analytics, caching, graph data, and time-series data.

Key takeaways:

- Amazon S3 is ideal for object storage.
- Amazon EBS provides block storage for EC2.
- Amazon EFS supports shared Linux file systems.
- Amazon RDS simplifies relational database management.
- Amazon DynamoDB supports highly scalable NoSQL workloads.
- Amazon Redshift is optimized for analytics.
- Security, backups, and monitoring are critical in every AWS environment.

## Additional Learning Resources

- [Amazon S3 documentation](https://docs.aws.amazon.com/s3/)
- [Amazon EBS documentation](https://docs.aws.amazon.com/ebs/)
- [Amazon EFS documentation](https://docs.aws.amazon.com/efs/)
- [Amazon RDS documentation](https://docs.aws.amazon.com/rds/)
- [Amazon Aurora documentation](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/)
- [Amazon DynamoDB documentation](https://docs.aws.amazon.com/dynamodb/)
- [Amazon Redshift documentation](https://docs.aws.amazon.com/redshift/)
- [Amazon ElastiCache documentation](https://docs.aws.amazon.com/elasticache/)
- [Migrating from Amazon QLDB to Amazon Aurora PostgreSQL](https://docs.aws.amazon.com/qldb/latest/developerguide/migration.html)

## Recommended Practice

- Create an S3 bucket.
- Launch an RDS instance in a test environment.
- Configure a DynamoDB table.
- Create and restore an EBS snapshot.
- Monitor storage and database services with CloudWatch.
