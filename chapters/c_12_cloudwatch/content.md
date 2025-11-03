# CloudWatch

CloudWatch is a monitoring and observability service that collects your resource data and provides actionable insights into your applications. With CloudWatch, you can respond to system-wide performance changes, optimize resource usage, and get a unified view of operational health.

You can use CloudWatch to do the following:

- Detect anomalous behavior in your environments.
- Set alarms to alert you when something is not right.
- Visualize logs and metrics with the AWS Management Console.
- Take automated actions like scaling.
- Troubleshoot issues.
- Discover insights to keep your applications healthy.

## Processes

![Cloudwatch processes](resources/cloudwatch_processes.png)

- __Amazon Cloudwatch__

    Complete visibility into your cloud resources and applications.

- __Collect__

    Collect metrics and logs from your resources, applications, and services that run on AWS or on-premises servers. 

- __Monitor__

    Visualize applications and infrastructure with dashboards. Troubleshoot with correlated logs and metrics, and set alerts. 

- __Act__

    Automate responses to operational changes with CloudWatch events and auto scaling. 

- __Analyze__ 

    Up to 1-second metrics, extended data retention (15 months), and real-time analysis with CloudWatch metric math.

Many AWS services automatically send metrics to CloudWatch for free at a rate of 1 data point per metric per 5-minute interval. This is called basic monitoring, and it gives you visibility into your systems without any extra cost. For many applications, basic monitoring is adequate.

For applications running on EC2 instances, you can get more granularity by posting metrics every minute instead of every 5-minutes using a feature like detailed monitoring. Detailed monitoring incurs a fee. For more information about pricing, see "Amazon CloudWatch Pricing" in the Resources section at the end of this lesson.

## CloudWatch concepts

A metric represents a time-ordered set of data points that are published to CloudWatch. Think of a metric as a variable to monitor and the data points as representing the values of that variable over time. Every metric data point must be associated with a timestamp.

![CloudWatch metrics](resources/cw_metric.png)

- __Metric__

    Metrics are data about the performance of your systems.

    For example, the CPU usage of a particular EC2 instance is one metric provided by Amazon EC2.

- __Timestamp__

    Each metric data point must be associated with a timestamp. If you do not provide a timestamp, CloudWatch creates one for you based on the time the data point was received.

AWS services that send data to CloudWatch attach dimensions to each metric. A dimension is a name and value pair that is part of the metric’s identity. You can use dimensions to filter the results that CloudWatch returns. For example, many Amazon EC2 metrics publish InstanceId as a dimension name and the actual instance ID as the value for that dimension.

By default, many AWS services provide metrics at no charge for resources such as EC2 instances, Amazon Elastic Block Store (Amazon EBS) volumes, and Amazon RDS database (DB) instances. For a charge, you can activate features such as detailed monitoring or publishing your own application metrics on resources such as your EC2 instances. 