# Architecture

## RDS or DynamoDB

When choosing between DynamoDB and RDS for an e-commerce platform, consider these key factors:  

1. Data Structure: RDS is better for complex, relational data with foreign key constraints. For e-commerce, RDS provides stronger referential integrity for relationships between products, orders, and customers.  

1. Query Complexity: RDS supports complex joins and queries, which are crucial for e-commerce operations like product searches, order history, and inventory management.

1. Transaction Requirements: If you need ACID transactions and complex transaction logic, RDS is more suitable.

1. Scalability: While DynamoDB scales easily, RDS might require more careful scaling strategies for complex e-commerce workloads.

1. Data Access Patterns: RDS is preferable when you have varied and complex data access patterns typical in e-commerce platforms.
