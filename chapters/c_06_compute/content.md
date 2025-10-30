# Compute

## On-Demand Instances

With On-Demand Instances, you pay for compute capacity per hour or per second, depending on which instances that you run. There are no long-term commitments or upfront payments required. Billing begins whenever the instance is running, and billing stops when the instance is in a stopped or terminated state. You can increase or decrease your compute capacity to meet the demands of your application and only pay the specified hourly rates for the instance that you use.

On-Demand Instances are recommended for the following use cases:

- Users who prefer the low cost and flexibility of Amazon EC2 without upfront payment or long-term commitments
- Applications with short-term, spiky, or unpredictable workloads that cannot be interrupted
- Applications being developed or tested on Amazon EC2 for the first time

## Spot Instances

For applications that have flexible start and end times, Amazon EC2 offers the Spot Instances option. With Amazon EC2 Spot Instances, you can request spare Amazon EC2 computing capacity for up to 90 percent off the On-Demand price. Spot Instances are recommended for the following use cases:

- Applications that have flexible start and end times
- Applications that are only feasible at very low compute prices
- Users with fault-tolerant or stateless workloads

With Spot Instances, you set a limit on how much you want to pay for the instance hour. This is compared against the current Spot price that AWS determines. Spot Instance prices adjust gradually based on long-term trends in supply and demand for Spot Instance capacity. If the amount that you pay is more than the current Spot price and there is capacity, you will receive an instance.

## Savings Plans

Savings Plans are a flexible pricing model that offers low usage prices for a 1-year or 3-year term commitment to a consistent amount of usage. Savings Plans apply to Amazon EC2, AWS Lambda, and AWS Fargate usage and provide up to 72 percent savings on AWS compute usage.

For workloads that have predictable and consistent usage, Savings Plans can provide significant savings compared to On-Demand Instances. Savings Plans are recommended for the following use cases:

- Workloads with a consistent and steady-state usage
- Customers who want to use different instance types and compute solutions across different locations
- Customers who can make monetary commitment to use Amazon EC2 over a 1-year or 3-year term

## Reserved Instances

For applications with steady state usage that might require reserved capacity, Amazon EC2 offers the Reserved Instances option. With this option, you save up to 72 percent compared to On-Demand Instance pricing. You can choose between three payment options: All Upfront, Partial Upfront, or No Upfront. You can select either a 1-year or 3-year term for each of these options.

With Reserved Instances, you can choose the type that best fits your applications needs.

- Standard Reserved Instances: These provide the most significant discount (up to 72 percent off On-Demand pricing) and are best suited for steady-state usage.
- Convertible Reserved Instances: These provide a discount (up to 54 percent off On-Demand pricing) and the capability to change the attributes of the Reserved Instance if the exchange results in the creation of Reserved Instances of equal or greater value. Like Standard Reserved Instances, Convertible Reserved Instances are best suited for steady-state usage.
- Scheduled Reserved Instances: These are available to launch within the time windows that you reserve. With this option, you can match your capacity reservation to a predictable recurring schedule that only requires a fraction of a day, a week, or a month.

## Dedicated Hosts

A Dedicated Host is a physical Amazon EC2 server that is dedicated for your use. Dedicated Hosts can help you reduce costs because you can use your existing server-bound software licenses, such as Windows Server, SQL Server, and Oracle licenses. And they can also help you meet compliance requirements. Amazon EC2 Dedicated Host is also integrated with AWS License Manager, a service that helps you manage your software licenses, including Microsoft Windows Server and Microsoft SQL Server licenses.

- Dedicated Hosts can be purchased on demand (hourly).
- Dedicated Hosts can be purchased as a Reservation for up to 70 percent off the On-Demand price.

## Instance classes

The __instance type__ is encoded as:

```bnf
<instance_type> ::= <instance_family>.<instance_size>

instance_family ::= <series><generation><options>
```

### Series

- __General purpose__:
  - __M__ - General purpose
  - __Mac__ - macOS
  - __T__ - Burstable performance

- __Compute optimized__:
  - __C__ - Compute optimized

- __Memory optimized__:
  - __R__ - Memory optimized
  - __X__ - Memory intensive
  - __z__ - High memory
  - __U__ - High memory
  - __U-__ - High memory

- __Storage optimized__:
  - __D__ - Dense storage
  - __H__ - not documented
  - __I__ - Storage optimized
  - __Im__ - Storage optimized (1 to 4 ratio of vCPU to memory)
  - __Is__ - Storage optimized (1 to 6 ratio of vCPU to memory)

- __Accelerated computing__:
  - __DL__ - not documented
  - __F__ - FPGA
  - __G__ - Graphics intensive
  - __Gr__ - not documented
  - __Inf__ - AWS Inferentia
  - __P__ - GPU accelerated
  - __Trn__ - AWS Trainium
  - __VT__ - Video transcoding

- __High-performace computing__:
  - __Hpc__

### Options

- __a__ - AMD Processors
- __b200__ - Accelerated by NVIDIA Blackwell GPUs
- __b__ - Block storage optimization
- __d__ - Instance store volumes
- __e-GB200__ - not documented
- __e__ - Extra storage or extra memory or extra GPU for accelerated computing instance types
- __f__ - not documented
- __flex__ - Flex instance
- __g__ - AWS Graviton processors
- __i__ - Intel processors
- __inh-32tb__ - not documented
- __m1ultra__ - Apple M1 Ultra chip
- __m2__ - Apple M2 chip
- __m2pro__ - Apple M2 Pro chip
- __m4pro__ - Apple M4 Pro chip
- __n__ - Network and EBS optimized
- __q__ - Qualcomm inference accelerators
- __tb1__ - not documented
- __u__ - not documented
- __z__ - High CPU frequency
- __`<nn>`tb__ - Amount of memory for high-memory instances (3 TiB to 32 TiB)
