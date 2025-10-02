# Domain 1: Development with AWS Services

Three tasks statements

1.1 Develop code for applications hosted on AWS (on EC2)
1.2 Develop code for AWS Lambda
1.3 Use data stores in application development


## Develop code for applications hosted on AWS

Review AWS Well-Architected Framework

Pillar: Operational Excellence


## Transcript

What architectural patterns do you write code for? 

First you have to understand the workload and the expected behaviors. Then you can design and build the applications along with insights for added visibility to the state and procedures to support. 
Here are a few questions to consider. 

- How will your application be accessed? 
- What are the usage patterns? Do you need to manage any hardware?
- What are your development and deployment patterns?
- How does your application work?
- And do you know how to develop, design, and implement code for an event-driven architecture?

### Event-driven designs 

Event-driven designs help to decouple your services, and for this exam, you need to know the difference between tightly-coupled and loosely-coupled components.

Event-driven designs promote the use of microservices and most AWS services generate events and many of the services can act as an event source. Event-driven designs provide scalable, resilient, agile, and cost-effective solutions. You can take this further and use AWS serverless services such as Amazon SQS, SNS, EventBridge to code and build event-driven applications.

But there are trade-offs to consider too. Unlike monolithic applications that process everything within the same memory on a single device, event-driven applications communicate across networks. When you have microservices, you get the benefit of having the parts fail independently and you can write your application code to handle the failures. And it is best practice to code applications to handle component failures.

Your application code should include failure detection and automatic remediation, so maybe you choose to use exponential back off with jitter. What does this technique increase for your application? Well, it increases the reliability and it also reduces operational costs, but it's not always safe to retry because that retry could increase the load on an already overloaded system. So what could you try instead? Instead of retrying immediately, you could use exponential backoff, which uses longer wait times and then vice versa. If backoff retries are still happening, use jitter because backoff retries can add to the overload and cause contention.

What about message failures? What do you add to your application code to handle message failures, including destinations and dead-letter queues? You can use Lambda to send invocations to other services like SQS, EventBridge, or SNS.

You could also use AWS Step Functions to separate retries, backoff rates, max attempts, intervals, and timeouts.

The point is to code and build resilience into your applications and workloads to withstand failures across components. Diving deeper, many applications use the event-driven architectures to manage the complexity of the components in system integrations. Understand how to use Step Functions instead of directly invoking systems to perform your task. You can also use Step Functions to monitor a workflow design.

### Orchestration

Workflows that involve branching logic, different types of failure models, and retries usually use an orchestrator to help keep track of the state and overall execution. You can use Lambda or implement messaging patterns to help orchestrate workflows in your application, but as your functions become more complex, you can migrate the logic to a state machine and Step Functions instead. Step Functions can also be used to orchestrate workflows and can handle nested workflow logic, errors, and retries. A key point and reason you need to dive deeper into different AWS services you could use is, for example, Step Functions workflows can run up to 1 year and can maintain different versions, which helps you to upgrade your code and requires less custom code. 

But if you need to coordinate state changes across multiple services, Amazon EventBridge might be a better choice. 

### Fan-out

If your application needs to publish messages to multiple endpoints, such as SQS, Data Firehose, HTTPS endpoints, or Lambda functions, you can use a fanout pattern. 

Know how to use fanout to replicate data sent to your production with your test environment to improve and test your application using that data received. 

What if you need to prevent duplicated, inconsistent, or loss of data?

Well, you have to design the code to properly validate input messages, calls, events, and so on, and identify if events were processed.

You can add idempotent function logic to Lambda to reduce unnecessary API calls, code processing time, data inconsistency, throttle, and latency. 

Know how to ensure the original API requests complete successfully and that subsequent retries will have no additional effect.

Also, dive deep and understand the differences between synchronous and asynchronous patterns, and understand that replication for AWS services. Since applications generate messages in the forms of calls to functions, services, and APIs, the communication can affect the performance, resources, and execution of tasks for the application.

Here are a few questions to consider.

- What type of workflows can you use in Step Functions: asynchronous workflows or synchronous workflows? It's actually both. 

- What if you use a REST API? Well, they are usually designed with synchronous communications where the response is required. 

- What if a service crashes while synchronous processing is happening? Well, that information is usually lost, but you can add code to your design to explicitly persist an incoming message after receiving it.

- What could you use for this? Well, one solution is SQS because SQS messages can be retained.

- What about stateless and stateful designs? Both store state from client request on the server and use that state to process other requests. Both use the database as a backend and the session is stored on the server. But stateful applications do not make a call to the database on that second request, which increases performance. Know how each scales.

- What about stateless and stateful applications using containers? Usually containers are stateless and add scalability and high availability because container orchestration and load balancing can add instances as demand increases.

For the exam, understand the scalability requirements and the requirements for the application or scenario questions and be able to choose the best design. 

For example, if you are building a new Docker application using ECS and you need to allow containers to access ports on the host container instance to send and receive traffic using port mapping, which component of ECS should you configure to implement this task? The container agent, the container instance, the task definition, or the agent? For this exam, you will need depth into the AWS services to answer questions like this. Port mappings are part of the container definition and are configured in the task definition.

Let's dive into more AWS specifics.

You can code and control your infrastructure whether you're developing your application in AWS or orchestrating resources for your application in AWS. Dive deeper into the AWS SDKs. Understand how using SDKs to integrate applications with AWS APIs reduces the complexity of authentication, retries, error handling, and more.

Also ensure you're familiar with the code examples provided by the SDK or the service. And understand how to write code that interacts with AWS services by using APIs and AWS SDKs.

- What AWS service could you use for developing and building serverless applications along with the toolkits we just mentioned? 
- How about the AWS Serverless Application Model? 

But I would also dive deeper into microservices design patterns using:

- Amazon ECS,
- Lambda,
- Cognito,
- API Gateway,
- CloudFront,
- Amazon DynamoDB, and
- S3.

Let's say you're a developer and your organization is migrating to AWS. As part of the migration, you have been tasked to build a new serverless architecture that will share memory and timeouts between the resources, such as Lambda, API Gateway, and DynamoDB, and also deploy all resources in a single-versioned application. 

- Which AWS service would you use: CloudFormation, OpsWorks, Elastic Beanstalk, or the Serverless Application Model? CloudFormation would work, but SAM simplifies the deployment and provides a simplified way of defining the API Gateway APIs, the Lambda functions, and DynamoDB tables needed by your serverless application.

- What service can help you create, publish, extend, maintain, and monitor your APIs? Ensure you have the depth needed for API Gateway. It features heavily throughout this exam.

For example, know how to:

- override status codes,
- enforce validation rules, and
- response transformations.
- Ensure you know and understand:
    - method requests and responses,
    - integration requests and responses,
    - mapping templates,
    - stages and
    - stage variables,
    - caches, and
    - throttling for API Gateway.
    - Usage plans and API keys.

What if you designed an online school application to use API Gateway with a non-proxy Lambda integration, and you now have to expose a GET method on a new course resource to invoke the Lambda function, which would allow users to grab a list of online courses, but the user must include a query string parameter in the request to get the data in online courses?
Do you configure a method request or method response of the resource?
You would need to configure the method request and it would need the required query parameter to process. How would you handle data streaming with your application code or design? 

### Streaming

In AWS, you can use managed streaming data services like Kinesis, or deploy and manage your own streaming data on Amazon EC2. Ensure you understand the challenges of adding streaming data to your application, such as the requirement for layers for storage and processing, and you have to plan for scalability, data durability, and fault tolerance in both layers. AWS also provides other platforms with the needed infrastructure to build streaming data applications: 

- Amazon Kinesis Data Streams,
- Amazon Data Firehose,
- Amazon Managed Streaming for Apache Kafka,
- Apache Flume,
- Apache Spark Streaming, and
- Apache Storm.

### Developing phase

There is a lot to the development phase:

- You need to write your code,
- know which development tools to use,
- use a source code repository,
- add storage for your application data,
- and integrate other tools and services.

As your development grows, you may need more tools, services, capacity, and so on.
 
Let's move on to the build of your development. This too requires a lot:

- compilation,
- resource generation,
- packaging,
- storing the build artifacts.

And for larger applications, there are additional dependencies. And we'll talk more about CodeBuild under the deployment domain, but dive deeper into CodeBuild also for this task statement.

Next, ensure you understand writing and running unit tests in your development environment. 

- What services could we use for testing? Dive deeper into:
    - AWS SAM,
    - CodePipeline, and
    - CloudFormation.

And dive deeper into automating your test environments.

This exam requires depth in developing and integrating AWS services, features, tools, and using the CLI.

Here's a question to consider: What if your application is gaining popularity and you now need to ensure syncing of the user profile data across devices to improve your user experience? 
 
Would you integrate AWS Amplify, Cognito identity pools, Cognito user pools, or Cognito Sync?
Cognito Sync is a client library that cross syncs devices of application user data, and this adds less complexity because you can use it to synchronize user profile data across multiple devices and the internet without requiring your own backend.

How about this one? I'll give you a hint: We talked about this earlier. For your application, you have recently noticed errors and that the read and the writes to your DynamoDB table are being throttled. As an excellent developer, you start troubleshooting and check CloudWatch. However, the consume capacity units have not exceeded your provisioned capacity units. You continue to investigate and find that the issue is from a hot partition in your DynamoDB table. This partition is accessed by your downstream application more frequently than the other partitions. How do you resolve this issue? Increase your read and write capacity for your table. Implement sharding to distribute workloads more evenly. Use DynamoDB Accelerator, or DAX. Implement error retries and exponential backoff. Or refactor your application to distribute your read and write operations evenly across the table. Well, you should know that when partitions are throttled, you need to optimize your table. Also, implementing retries and exponential backoff uses longer waits between retries for consecutive error response and this helps improve reliability. And here's an extra tip: If you're using an AWS SDK, this logic is built in. If you're using another SDK, then you need to implement this manually. 

### Other services

For this exam, ensure you know how to have consistent development tests and production environments with increasing levels of operations control. Dive deeper and understand how and when to use AWS services in your microservice architecture, such as:

- Amazon SQS,
- Amazon SNS,
- Amazon Kinesis Data Streams,
- Amazon Kinesis services,
- Amazon DynamoDB Streams,
- the AWS Internet of Things,
- Amazon MQ, and
- AWS Step Functions 
