# Databases on AWS

## Introduction

### Relational databases

#### Benefits

- __Complex SQL__: Use SQL to join multiple tables so you can better understand relationships between your data.

- __Reduced redundancy__: You can store data in one table and reference it from other tables instead of saving the same data in different places. (Leo's note: Normal Forms)

- __Familiarity__: Because relational databases have been a popular choice since the 1970s, technical professionals often have familiarity and experience with them.

- __Accuracy__: Relational databases ensure that your data has high integrity and adheres to the atomicity, consistency, isolation, and durability (ACID) principle. (Leo's note: There's a relational model that holds semantics.)

#### Use cases

- __Applications that have a fixed schema__:

    These are applications that have a fixed schema and don't change often. An example is a lift-and-shift application that lifts an app from on-premises and shifts it to the cloud, with little or no modifications.

- __Applications that need persistent storage__

    These are applications that need persistent storage and follow the ACID principle, such as:
      - Enterprise resource planning (ERP) applications
      - Customer relationship management (CRM) applications
      - Commerce and financial applications

#### Managed vs Unmanaged

Managed compared to unmanaged can be understood as a trade-off between convenience and control.

![Responsibility model for unmanaged dbs](resources/OnPrem_vs_EC2.png)

To shift more of the work to AWS, you can use a managed database service. These services provide the setup of both the EC2 instance and the database, and they provide systems for high availability, scalability, patching, and backups. However, in this model, you’re still responsible for database tuning, query optimization, and ensuring that your customer data is secure. This option provides the ultimate convenience but the least amount of control compared to the two previous options.

![Responsibility model for AWS managed dbs](resources/Managed_DB.png)

### Database Instances

The compute portion is called database instance.

- __Standard classes__: (includes m classes)

  Standard instances provide a balance of compute, memory, and network resources. They are a good choice for many database workloads.

- __Memory optimized classes__: (includes r and x classes)

Memory optimized instances accelerate performance for workloads that process large datasets in memory.

- __Burstable classes__: (includes t classes)

Burstable performance instances provide a baseline level of CPU performance with the ability to burst above the baseline.

### Storage on Amazon RDS

The storage portion of DB instances for Amazon RDS use Amazon Elastic Block Store (Amazon EBS) volumes for database and log storage. This includes MySQL, MariaDB, PostgreSQL, Oracle, and SQL Server.

When using Aurora, data is stored in cluster volumes, which are single, virtual volumes that use solid-state drives (SSDs). A cluster volume contains copies of your data across three Availability Zones in a single AWS Region. For nonpersistent, temporary files, Aurora uses local storage.

Amazon RDS provides three storage types: General Purpose SSD (also called gp2 and gp3), Provisioned IOPS SSD (also called io1), and Magnetic (also called standard). They differ in performance characteristics and price, which means you can tailor your storage performance and cost to the needs of your database workload.

- __General Purpose SSD__

    These volumes offer cost-effective storage. This is ideal for a broad range of workloads running on medium-sized DB instances. General Purpose storage is best suited for development and testing environments.

- __Provisioned IOPS SSD__

    This type of storage is designed to meet the needs of I/O-intensive workloads. For example, database workloads requiring low I/O latency and consistent I/O throughput. Provisioned IOPS storage is best suited for production environments.

- __Magnetic__

    Amazon RDS also supports magnetic storage for backward compatibility. We recommend that you use General Purpose SSD or Provisioned IOPS SSD for any new storage needs. The maximum amount of storage for DB instances on magnetic storage is less than that of the other storage types.

### Amazon RDS in an Amazon Virtual Private Cloud

When you create a DB instance, you select the Amazon Virtual Private Cloud (Amazon VPC) your databases will live in. Then, you select the subnets that will be designated for your DB. This is called a DB subnet group, and it has at least two Availability Zones in its Region. The subnets in a DB subnet group should be private, so they don’t have a route to the internet gateway. This ensures that your DB instance, and the data inside it, can be reached only by the application backend.

Access to the DB instance can be restricted further by using network access control lists (network ACLs) and security groups. With these firewalls, you can control, at a granular level, the type of traffic you want to provide access into your database.

Using these controls provides layers of security for your infrastructure. It reinforces that only the backend instances have access to the database.

### Backups

- __Automated backups__

    Automated backups are turned on by default. This backs up your entire DB instance (not just individual databases on the instance) and your transaction logs. When you create your DB instance, you set a backup window that is the period of time that automatic backups occur. Typically, you want to set the window during a time when your database experiences little activity because it can cause increased latency and downtime.

    Retaining backups: Automated backups are retained between 0 and 35 days. You might ask yourself, “Why set automated backups for 0 days?” The 0 days setting stops automated backups from happening. If you set it to 0, it will also delete all existing automated backups. This is not ideal. The benefit of automated backups that you can do point-in-time recovery.

    Point-in-time recovery: This creates a new DB instance using data restored from a specific point in time. This restoration method provides more granularity by restoring the full backup and rolling back transactions up to the specified time range.

- __Manual snapshots__

    If you want to keep your automated backups longer than 35 days, use manual snapshots. Manual snapshots are similar to taking Amazon EBS snapshots, except you manage them in the Amazon RDS console. These are backups that you can initiate at any time. They exist until you delete them. For example, to meet a compliance requirement that mandates you to keep database backups for a year, you need to use manual snapshots. If you restore data from a manual snapshot, it creates a new DB instance using the data from the snapshot.

It is advisable to deploy both backup options. Automated backups are beneficial for point-in-time recovery. With manual snapshots, you can retain backups for longer than 35 days.

### Redundancy with Amazon RDS Multi-AZ

In an Amazon RDS Multi-AZ deployment, Amazon RDS creates a redundant copy of your database in another Availability Zone. You end up with two copies of your database—a primary copy in a subnet in one Availability Zone and a standby copy in a subnet in a second Availability Zone.

![Multi AZ DB](resources/Multi_AZ.png)

The primary copy of your database provides access to your data so that applications can query and display the information. The data in the primary copy is synchronously replicated to the standby copy. The standby copy is not considered an active database, and it does not get queried by applications.
Diagram depicting Amazon RDS Multi-AZ creating a redundant copy of a database in another Availability Zone.
To improve availability, Amazon RDS Multi-AZ ensures that you have two copies of your database running and that one of them is in the primary role. If an availability issue arises, such as the primary database loses connectivity, Amazon RDS initiates an automatic failover.
When you create a DB instance, a Domain Name System (DNS) name is provided. AWS uses that DNS name to fail over to the standby database. In an automatic failover, the standby database is promoted to the primary role, and queries are redirected to the new primary database.

To help ensure that you don't lose Multi-AZ configuration, there are two ways you can create a new standby database. They are as follows:

Demote the previous primary to standby if it's still up and running.
Stand up a new standby DB instance.
The reason you can select multiple subnets for an Amazon RDS database is because of the Multi-AZ configuration. You will want to ensure that you have subnets in different Availability Zones for your primary and standby copies.

### Amazon RDS security

When it comes to security in Amazon RDS, you have control over managing access to your Amazon RDS resources, such as your databases on a DB instance. How you manage access will depend on the tasks you or other users need to perform in Amazon RDS. Network ACLs and security groups help users dictate the flow of traffic. If you want to restrict the actions and resources others can access, you can use AWS Identity and Access Management (IAM) policies.

- __IAM__

    Use IAM policies to assign permissions that determine who can manage Amazon RDS resources. For example, you can use IAM to determine who can create, describe, modify, and delete DB instances, tag resources, or modify security groups

- __Security Groups__

    Use security groups to control which IP addresses or Amazon EC2 instances can connect to your databases on a DB instance. When you first create a DB instance, all database access is prevented except through rules specified by an associated security group.

- __Amazon RDS encryption__

    Use Amazon RDS encryption to secure your DB instances and snapshots at rest.

- __SSL or TLS__

    Use Secure Sockets Layer (SSL) or Transport Layer Security (TLS) connections with DB instances running the MySQL, MariaDB, PostgreSQL, Oracle, or SQL Server database engines.

## Purpose-built databases

- __Amazon DynamoDB__

    DynamoDB is a fully managed NoSQL database that provides fast, consistent performance at any scale. It has a flexible billing model, tight integration with infrastructure as code (IaC), and a hands-off operational model. DynamoDB has become the database of choice for two categories of applications: high-scale applications and serverless applications. Although DynamoDB is the database of choice for high-scale and serverless applications, it can work for nearly all online transaction processing (OLTP) application workloads.

- __Amazon ElastiCache__

    ElastiCache is a fully managed, in-memory caching solution. It provides support for two open-source, in-memory cache engines: Redis and Memcached. You aren’t responsible for instance failovers, backups and restores, or software upgrades.

- __Amazon MemoryDB for Redis__

MemoryDB is a Redis-compatible, durable, in-memory database service that delivers ultra-fast performance. With MemoryDB, you can achieve microsecond read latency, single-digit millisecond write latency, high throughput, and Multi-AZ durability for modern applications, like those built with microservices architectures. You can use MemoryDB as a fully managed, primary database to build high-performance applications. You do not need to separately manage a cache, durable database, or the required underlying infrastructure.

- __Amazon DocumentDB (with MongoDB compatibility)__

    Amazon DocumentDB is a fully managed document database from AWS. A document database is a type of NoSQL database you can use to store and query rich documents in your application. These types of databases work well for the following use cases: content management systems, profile management, and web and mobile applications. Amazon DocumentDB has API compatibility with MongoDB. This means you can use popular open-source libraries to interact with Amazon DocumentDB, or you can migrate existing databases to Amazon DocumentDB with minimal hassle.

- __Amazon Keyspaces (for Apache Cassandra)__

    Amazon Keyspaces is a scalable, highly available, and managed Apache Cassandra compatible database service. Apache Cassandra is a popular option for high-scale applications that need top-tier performance. Amazon Keyspaces is a good option for high-volume applications with straightforward access patterns. With Amazon Keyspaces, you can run your Cassandra workloads on AWS using the same Cassandra Query Language (CQL) code, Apache 2.0 licensed drivers, and tools that you use today.

- __Amazon Neptune__

    Neptune is a fully managed graph database offered by AWS. A graph database is a good choice for highly connected data with a rich variety of relationships. Companies often use graph databases for recommendation engines, fraud detection, and knowledge graphs.

- __Amazon Timestream__

    Timestream is a fast, scalable, and serverless time series database service for Internet of Things (IoT) and operational applications. It makes it easy to store and analyze trillions of events per day up to 1,000 times faster and for as little as one-tenth of the cost of relational databases. Time series data is a sequence of data points recorded over a time interval. It is used for measuring events that change over time, such as stock prices over time or temperature measurements over time.

- __Amazon Quantum Ledger Database (Amazon QLDB)__

    With traditional databases, you can overwrite or delete data, so developers use techniques, such as audit tables and audit trails to help track data lineage. These approaches can be difficult to scale and put the burden of ensuring that all data is recorded on the application developer. Amazon QLDB is a purpose-built ledger database that provides a complete and cryptographically verifiable history of all changes made to your application data.

## DynamoDB

![DynamoDB Icon](resources/DynamoDB_Icon.jpg)

DynamoDB is a fully managed NoSQL database service that provides fast and predictable performance with seamless scalability. With DynamoDB, you can offload the administrative burdens of operating and scaling a distributed database. You don't need to worry about hardware provisioning, setup and configuration, replication, software patching, or cluster scaling.

With DynamoDB, you can do the following:

- Create database tables that can store and retrieve any amount of data and serve any level of request traffic.
- Scale up or scale down your tables' throughput capacity without downtime or performance degradation. 
- Monitor resource usage and performance metrics using the AWS Management Console.

DynamoDB automatically spreads the data and traffic for your tables over a sufficient number of servers to handle your throughput and storage requirements. It does this while maintaining consistent, fast performance. All your data is stored on SSDs and is automatically replicated across multiple Availability Zones in a Region, providing built-in high availability and data durability.

### DynamoDB core components

In DynamoDB, tables, items, and attributes are the core components that you work with. A table is a collection of items, and each item is a collection of attributes. DynamoDB uses primary keys to uniquely identify each item in a table and secondary indexes to provide more querying flexibility.

- __Table__

    Similar to other database systems, DynamoDB stores data in tables. A table is a collection of data. For example, you can have a table called Person that you can use to store personal contact information about friends, family, or anyone else of interest. You can also have a Cars table to store information about vehicles that people drive.

- __Item__

    Each table contains zero or more items. An item is a group of attributes that is uniquely identifiable among all the other items. In a Person table, each item represents a person. In a Cars table, each item represents one vehicle. Items in DynamoDB are similar in many ways to rows, records, or tuples in other database systems. In DynamoDB, there is no limit to the number of items you can store in a table.

- __Attribute__

    Each item is composed of one or more attributes. An attribute is a fundamental data element, something that does not need to be broken down any further. For example, an item in a Person table might contain attributes called PersonID, LastName, FirstName, and so on. In a Department table, an item might have attributes such as DepartmentID, Name, Manager, and so on. Attributes in DynamoDB are similar in many ways to fields or columns in other database systems.

### DynamoDB use cases

DynamoDB is a fully managed service that handles the operations work. You can offload the administrative burdens of operating and scaling distributed databases to AWS.

You might want to consider using DynamoDB in the following circumstances:

- You are experiencing scalability problems with other traditional database systems.
- You are actively engaged in developing an application or service.
- You are working with an OLTP workload.
- You are deploying a mission-critical application that must be highly available at all times without manual intervention.
- You require a high level of data durability, regardless of your backup-and-restore strategy.

DynamoDB is used in a wide range of workloads because of its simplicity, from low-scale operations to ultrahigh-scale operations.

- __Develop software applications__

    Build internet-scale applications supporting user-content metadata and caches that require high concurrency and connections for millions of users and millions of requests per second.

- __Create media metadata stores__

    Scale throughput and concurrency for analysis of media and entertainment workloads, such as real-time video streaming and interactive content. Deliver lower latency with multi-Region replication across Regions.

- __Scale gaming platforms__

    Focus on driving innovation with no operational overhead. Build out your game platform with player data, session history, and leaderboards for millions of concurrent users.

- __Deliver seamless retail experiences__

    Use design patterns for deploying shopping carts, workflow engines, inventory tracking, and customer profiles. DynamoDB supports high-traffic, extreme-scaled events and can handle millions of queries per second.

### DynamoDB security

DynamoDB provides a number of security features to consider as you develop and implement your own security policies. They include the following:

- DynamoDB provides a highly durable storage infrastructure designed for mission-critical and primary data storage. Data is redundantly stored on multiple devices across multiple facilities in a DynamoDB Region.  
- All user data stored in DynamoDB is fully encrypted at rest. DynamoDB encryption at rest provides enhanced security by encrypting all your data at rest using encryption keys stored in AWS Key Management Service (AWS KMS).
- IAM administrators control who can be authenticated and authorized to use DynamoDB resources. You can use IAM to manage access permissions and implement security policies.
- As a managed service, DynamoDB is protected by the AWS global network security procedures.

Best practices:

- Use AWS CloudTrail to monitor AWS managed key usage: If you are using an AWS managed key for encryption at rest, usage of the key is recorded in AWS CloudTrail. CloudTrail can tell you who made the request, the services used, actions performed, parameters for the action, and response elements returned.

- Use IAM roles to authenticate access to DynamoDB: For users, applications, and other AWS services to access DynamoDB, they must include valid AWS credentials in their AWS API requests. Use IAM roles to obtain temporary access keys.

- Use IAM policy conditions for fine-grained access control: When you grant permissions in DynamoDB, you can specify conditions that determine how a permissions policy takes effect. Implementing least privilege is key in reducing security risk and the impact that can result from errors or malicious intent.

- Monitor DynamoDB operations using CloudTrail: When activity occurs in DynamoDB, that activity is recorded in a CloudTrail event. For an ongoing record of events in DynamoDB and in your AWS account, create a trail to deliver log files to an Amazon Simple Storage Service (Amazon S3) bucket.

## AWS database services

Quick look at the AWS database portfolio. 

|AWS Service(s) | Database Type| Use Cases
|-|-|-
|Amazon RDS, Aurora, Amazon Redshift | Relational|Traditional applications, ERP, CRM, ecommerce
| DynamoDB | Key-value | High-traffic web applications, ecommerce systems, gaming applications
| Amazon ElastiCache for Memcached, Amazon ElastiCache for Redis | In-memory | Caching, session management, gaming leaderboards, geospatial applications
| Amazon DocumentDB | Document | Content management, catalogs, user profiles
| Amazon Keyspaces | Wide column | High-scale industrial applications for equipment maintenance, fleet management, route optimization
| Neptune | Graph | Fraud detection, social networking, recommendation engines
| Timestream | Time series | IoT applications, Development Operations (DevOps), industrial telemetry
| Amazon QLDB | Ledger | Systems of record, supply chain, registrations, banking transactions
