# AWS Core Concepts and Compute Services

## What is AWS?

Amazon Web Services (AWS) is a cloud computing platform that provides on-demand IT resources such as:

- Compute power
- Storage
- Databases
- Networking
- Security
- Analytics
- Machine learning

AWS allows companies to build and deploy applications without managing physical infrastructure.

---

# Cloud Computing Basics

## What is Cloud Computing?

Cloud computing is the delivery of computing services over the internet instead of using local servers or personal computers.

### Benefits of Cloud Computing

- Pay-as-you-go pricing
- Scalability
- High availability
- Global infrastructure
- Faster deployment
- Reduced hardware costs

---

# Types of Cloud Computing

## 1. Infrastructure as a Service (IaaS)

Provides virtualized infrastructure.

Examples:
- Amazon EC2
- Amazon VPC
- Amazon EBS

## 2. Platform as a Service (PaaS)

Provides platforms for application development.

Examples:
- AWS Elastic Beanstalk
- AWS Lambda

## 3. Software as a Service (SaaS)

Provides fully managed software over the internet.

Examples:
- Gmail
- Microsoft 365

---

# AWS Global Infrastructure

AWS infrastructure consists of:

## Regions

A physical geographic area containing multiple Availability Zones.

Example:
- us-east-1
- eu-west-1

## Availability Zones (AZs)

Data centers within a region designed for fault isolation.

## Edge Locations

Used by CloudFront for content delivery and low latency.

---

# Shared Responsibility Model

## AWS Responsibilities

AWS manages:
- Physical security
- Hardware
- Networking
- Data centers

## Customer Responsibilities

Customers manage:
- IAM permissions
- Data encryption
- Operating systems
- Applications

---

# AWS Identity and Access Management (IAM)

IAM controls access to AWS resources.

## IAM Components

### Users
Individual accounts for people or applications.

### Groups
Collection of users with shared permissions.

### Roles
Temporary access permissions assigned to services or users.

### Policies
JSON documents that define permissions.

---

# AWS Compute Services

Compute services provide processing power for applications.

---

# Amazon EC2 (Elastic Compute Cloud)

EC2 provides virtual servers in the cloud.

## EC2 Features

- Resizable compute capacity
- Multiple operating systems
- Secure and scalable
- Pay only for usage

## EC2 Instance Types

### General Purpose
Balanced compute, memory, and networking.

Example:
- t3.micro

### Compute Optimized
High-performance processors.

Example:
- c5.large

### Memory Optimized
Large memory workloads.

Example:
- r5.large

### Storage Optimized
High disk throughput.

Example:
- i3.large

---

# EC2 Pricing Models

## On-Demand

Pay per second/hour without long-term commitment.

## Reserved Instances

Lower pricing for long-term commitments.

## Spot Instances

Unused AWS capacity at discounted prices.

## Dedicated Hosts

Physical servers dedicated to one customer.

---

# Amazon Machine Image (AMI)

An AMI is a template used to launch EC2 instances.

It contains:
- Operating system
- Applications
- Configurations

---

# Security Groups

Acts as a virtual firewall for EC2 instances.

## Characteristics

- Stateful
- Allow rules only
- Controls inbound and outbound traffic

---

# Network ACLs (NACLs)

Subnet-level security layer.

## Characteristics

- Stateless
- Allow and deny rules
- Controls subnet traffic

---

# Elastic Load Balancer (ELB)

Distributes traffic across multiple targets.

## Types of Load Balancers

### Application Load Balancer (ALB)
Layer 7 HTTP/HTTPS traffic.

### Network Load Balancer (NLB)
High-performance Layer 4 traffic.

### Gateway Load Balancer
Used with virtual appliances.

---

# Auto Scaling

Automatically adjusts EC2 capacity based on demand.

## Benefits

- High availability
- Cost optimization
- Automatic scaling

---

# AWS Lambda

Serverless compute service that runs code without managing servers.

## Lambda Features

- Event-driven
- Automatic scaling
- Pay per execution
- Supports multiple programming languages

## Common Use Cases

- APIs
- Automation
- File processing
- Event handling

---

# AWS Elastic Beanstalk

Platform as a Service (PaaS) for deploying applications.

## Features

- Automated deployment
- Auto scaling
- Monitoring integration
- Supports multiple languages

---

# Amazon ECS (Elastic Container Service)

Container orchestration service for Docker containers.

## ECS Components

### Cluster
Logical grouping of resources.

### Task Definition
Blueprint for containers.

### Service
Maintains desired number of running tasks.

---

# Amazon EKS (Elastic Kubernetes Service)

Managed Kubernetes service on AWS.

## Benefits

- Managed Kubernetes control plane
- High availability
- Integration with AWS services

---

# AWS Fargate

Serverless compute engine for containers.

## Benefits

- No server management
- Automatic scaling
- Works with ECS and EKS

---

# Monitoring and Logging

## Amazon CloudWatch

Monitoring service for AWS resources.

### Features

- Metrics
- Logs
- Alarms
- Dashboards

---

# AWS CloudTrail

Tracks API activity and account actions.

## Use Cases

- Auditing
- Security monitoring
- Compliance

---

# AWS Well-Architected Framework

Guidelines for building secure and efficient cloud systems.

## Pillars

1. Operational Excellence
2. Security
3. Reliability
4. Performance Efficiency
5. Cost Optimization
6. Sustainability

---

# Best Practices

- Use least privilege access
- Enable Multi-Factor Authentication (MFA)
- Monitor resources with CloudWatch
- Use Auto Scaling for availability
- Regularly back up data
- Tag AWS resources properly

---

# Summary

AWS provides scalable and reliable cloud services for modern applications.

Core concepts include:
- Cloud computing
- Global infrastructure
- IAM and security
- Compute services
- Monitoring and scaling

Key compute services include:
- EC2
- Lambda
- ECS
- EKS
- Elastic Beanstalk
- Fargate

Understanding these services is essential for cloud engineering and DevOps roles.
