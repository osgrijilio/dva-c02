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
