# Questions

## 1

 Each time a developer publishes a new version of an AWS Lambda function, all the dependent event source mappings need to be updated with the reference to the new version’s Amazon Resource Name (ARN). These updates are time consuming and error-prone.

Which combination of actions should the developer take to avoid performing these updates when publishing a new Lambda version? (Select TWO.)

- [ ] A Update event source mappings with the ARN of the Lambda layer.

- B Point a Lambda alias to a new version of the Lambda function.

- C Create a Lambda alias for each published version of the Lambda function.

- D Point a Lambda alias to a new Lambda function alias.

- E Update the event source mappings with the Lambda alias ARN.

Correct answers:

- B: Point a Lambda alias to a new version of the Lambda function.

    A Lambda alias is a pointer to a specific Lambda function version.

    For more information about creating and using Lambda function aliases, see Lambda function aliases.

- E: Update the event source mappings with the Lambda alias ARN.

    Instead of using ARNs for the Lambda function in event source mappings, you can use an alias ARN. You do not need to update your event source mappings when you promote a new version or roll back to a previous version.

    For more information about creating and using Lambda function aliases, see Lambda function aliases.

## 2

A company is working on a project to enhance its serverless application development process. The company hosts applications on AWS Lambda. The development team regularly updates the Lambda code and wants to use stable code in production.

Which combination of steps should the development team take to configure Lambda functions to meet both development and production requirements? (Select TWO.)

- A: Create a new Lambda layer every time a new code release needs testing.

- B: Create a new Lambda version every time a new code release needs testing.

- C: Create two Lambda function aliases. Name one as Production and the other as Development. Point the Production alias to a production-ready Lambda layer Amazon Resource Name (ARN). Point the Development alias to the $LATEST layer ARN.

- D: Create two Lambda function aliases. Name one as Production and the other as Development. Point the Production alias to a production-ready qualified Amazon Resource Name (ARN) version. Point the Development alias to the $LATEST version.

- E: Create two Lambda function aliases. Name one as Production and the other as Development. Point the Production alias to the production-ready unqualified Amazon Resource Name (ARN) version. Point the Development alias to the variable LAMBDA_TASK_ROOT.

Correct answers:

- B: Create a new Lambda version every time a new code release needs testing.

    Lambda function versions are designed to manage deployment of functions. They can be used for code changes, without affecting the stable production version of the code.

    For more information about Lambda function versions, see Lambda function versions.

- D: Create two Lambda function aliases. Name one as Production and the other as Development. Point the Production alias to a production-ready qualified Amazon Resource Name (ARN) version. Point the Development alias to the $LATEST version.

    By creating separate aliases for Production and Development, systems can initiate the correct alias as needed. A Lambda function alias can be used to point to a specific Lambda function version. Using the functionality to update an alias and its linked version, the development team can update the required version as needed. The $LATEST version is the newest published version.

    For more information about Lambda function aliases, see Lambda function aliases.

    For more information about Lambda function versions, see Lambda function versions.

## 3

A company uses an AWS Lambda function to call a third-party REST endpoint. Personally identifiable information (PII) is exposed upon a successful request. The third party that manages the REST endpoint requires the company to change the API key that the company uses to invoke the endpoint every 4 months.

The company retrieves the API key by calling an endpoint that the third party owns. The endpoint uses basic authentication (username and password). The new API key is available and active one month prior to the inactivation of the old API key. When the company retrieves the new API key, the company needs to store the key for use in future invocations of the REST endpoint. The company needs a secure solution that eliminates downtime while the company sets up the new API key.

Which solution will meet these requirements?

- A: Store the API key in Parameter Store, a capability of AWS Systems Manager, as a SecureString. Configure rotation to obtain the new API key from the third party and to update the parameter value.

- B: Store the API key in AWS Secrets Manager. Create a Lambda function to obtain the new API key from the third party. Configure rotation in Secrets Manager to use the Lambda function to obtain a new API key. Store the new API key in Secrets Manager. Configure rotation to occur every 4 months.

- C: Store the API key in an Amazon DynamoDB table. Create a Lambda function to retrieve the new API key from the third party and to update the value in DynamoDB. Use an Amazon EventBridge scheduled rule to invoke the Lambda function every 4 months.

- D: Store the API key as a Lambda environment variable. Retrieve the new API key from the third party by using open source software. Manually update the Lambda environment variable.

Correct answer:

- B: Store the API key in AWS Secrets Manager. Create a Lambda function to obtain the new API key from the third party. Configure rotation in Secrets Manager to use the Lambda function to obtain a new API key. Store the new API key in Secrets Manager. Configure rotation to occur every 4 months.

    API key rotation (including third-party key rotation with a Lambda function) is available in Secrets Manager.

    For more information about how to rotate third-party secrets, see How Rotation Works.
    <https://docs.aws.amazon.com/secretsmanager/latest/userguide/rotating-secrets.html#rotate-secrets_how>

## 4

A developer builds an inventory application that runs on employee tablets. The tablet application serves as an activity worker for an AWS Step Functions state machine. The application must retrieve a scheduled task, periodically report on task progress, and report task completion or task failure.

Which Step Functions API actions does the tablet application need to make?

- A: StartExecution, GetActivityTask, SendTaskHeartbeat, StopExecution

- B: CreateActivity, SendTaskHeartbeat, SendTaskFailure, SendTaskSuccess

- C: CreateActivity, SendTaskHeartbeat, DeleteActivity

- D: CreateActivity, GetActivityTask, SendTaskHeartbeat, SendTaskFailure, SendTaskSuccess

Correct answer

- D: CreateActivity, GetActivityTask, SendTaskHeartbeat, SendTaskFailure, SendTaskSuccess

    The activity worker must first call the CreateActivity API action to obtain the activity Amazon Resource Name (ARN). The GetActivityTask API action then retrieves a scheduled task. The SendTaskHeartbeat API action periodically reports on task progress. The SendTaskFailure or SendTaskSuccess API actions report success or failure.

    For more information about the CreateActivity API action, see CreateActivity.

    For more information about the GetActivityTask API action, see GetActivityTask.

    For more information about the SendTaskHeartbeat API action, see SendTaskHeartbeat.

    For more information about the SendTaskSuccess API action, see SendTaskSuccess.

    For more information about the SendTaskFailure API action, see SendTaskFailure.

## 5

A developer has written several custom applications that read and write to the same Amazon DynamoDB table. Each time the data in the DynamoDB table is modified, this change should be sent to an external API.

Which combination of steps should the developer perform to accomplish this task? (Select TWO.)

- A: Enable DynamoDB Streams on the table.

- B: Configure an event in Amazon EventBridge that publishes the change to an Amazon Managed Streaming for Apache Kafka (Amazon MSK) data stream.

- C: Create a trigger in the DynamoDB table to publish the change to an Amazon Kinesis data stream.

- D: Deliver the stream to an Amazon Simple Notification Service (Amazon SNS) topic and subscribe the API to the topic.

- E: Configure an AWS Lambda function to be triggered by the DynamoDB stream and call the external API.

Correct answer:

- A: Enable DynamoDB Streams on the table.

    You can enable DynamoDB Streams on a table to create an event that invokes an AWS Lambda function.

    For more information about how to use DynamoDB Streams, see DynamoDB Streams and AWS Lambda Triggers.

- E: Configure an AWS Lambda function to be triggered by the DynamoDB stream and call the external API.

    With DynamoDB Streams, you can trigger a Lambda function to perform additional tasks. For example, an additional task could be calling an external API each time a DynamoDB table is updated.

    For more information about how to use DynamoDB Streams, see DynamoDB Streams and AWS Lambda Triggers.

## 6

A company is developing an image processing application. When an image is uploaded to an Amazon S3 bucket, a number of independent and separate services must be invoked to process the image. The services do not have to be available immediately, but they must process every image.

Which application design satisfies these requirements?

- A. Configure an Amazon S3 event notification that publishes to an Amazon SQS queue. Each service pulls the message from the same queue.

- B. Configure an Amazon S3 event notification that publishes to an Amazon SNS topic. Each service subscribes to the same topic.

- C. Configure an Amazon S3 event notification that publishes to an Amazon SQS queue. Subscribe a separate Amazon SNS topic for each service to an Amazon SQS queue.

- D. Configure an Amazon S3 event notification that publishes to an Amazon SNS topic. Subscribe a separate Amazon SQS queue for each service to the Amazon SNS topic.

Correct answer:

- D: Configure an Amazon S3 event notification that publishes to an Amazon SNS topic. Subscribe a separate Amazon SQS queue for each service to the Amazon SNS topic.

    Each service can subscribe to an individual Amazon SQS queue, which receives an event notification from the Amazon SNS topic. This is a fanout architectural implementation.

    For more information about Amazon SNS fanout architecture, see Common Amazon SNS scenarios

## 7

A developer configures AWS CodeDeploy to install an application on Amazon EC2 instances in an Amazon EC2 Auto Scaling group.

Where should the developer place the appspec.yml file?

- A: In the root of the directory structure of the application's source code
- B: Directly into the CodeDeploy console
- C: In the .ebextensions folder in the application's source code
- D: In the same Amazon S3 bucket as the application source code bundle

Correct answer

- A: In the root of the directory structure of the application's source code

    To deploy an application on EC2 instances, the appspec.yml file must be placed in the root of the directory structure of an application's source code.

    For more information about CodeDeploy appspec.yml file configuration when using EC2 instances, see CodeDeploy AppSpec File reference.

## 8

A developer wants to monitor invocations of an AWS Lambda function by using Amazon CloudWatch Logs. The developer added a number of print statements to the function code that write the logging information to the stdout stream. After running the function, the developer does not see any log data being generated.

Why does the log data NOT appear in the CloudWatch logs?

- A: The log data is not written to the stderr stream.

- B: Lambda function logging is not automatically enabled.

- C: The execution role for the Lambda function did not grant permissions to write log data to CloudWatch Logs.

- D: The Lambda function outputs the logs to an Amazon S3 bucket.

Correct answer

- C: The execution role for the Lambda function did not grant permissions to write log data to CloudWatch Logs.

    The function needs permission to call CloudWatch Logs. Update the execution role to grant the permission. You can use the managed policy of AWSLambdaBasicExecutionRole.

    For more information about troubleshooting execution issues in Lambda, see Troubleshoot execution issues in Lambda.

## 9

A developer built an application that stores data in an Amazon RDS Multi-AZ DB instance. The database performs reads and writes constantly and is responding slowly. The intensive read requests are received unpredictably several times each hour. The application cannot tolerate reading stale data. The developer must increase the retrieval speed for the intensive read requests.

Which strategy will meet these requirements?

- A. Use an Amazon ElastiCache cluster with a write-through strategy. Configure the application to direct the intensive read operations to ElastiCache.

- B. Use an Amazon DynamoDB Accelerator (DAX) cluster with a write-through strategy. Configure the application to direct the intensive read operations to the DAX cluster.

- C. Configure the application to direct the intensive read operations to the Multi-AZ standby replica in the second Availability Zone.

- D. Add an RDS read replica. Configure the application to direct the intensive read operations to the read replica.

Correct answer

- A. Use an Amazon ElastiCache cluster with a write-through strategy. Configure the application to direct the intensive read operations to ElastiCache.

    An ElastiCache cluster with a write-through strategy will allow for the read requests to be redirected to ElastiCache efficiently. The strategy will allow for the most up-to-date data to be retrieved.

    For more information about the ElastiCache write-through caching strategy, see Caching strategies.

## 10

A company has an inventory system that receives sporadic inventory updates from a fulfillment system in the form of large JSON files. While many files can be sent in a short time period, days can pass when no files are sent. The company wants to process these files as soon as they arrive.

Which solution will meet these requirements?

- A: Send the JSON files to Amazon Elastic File System (Amazon EFS). Configure an AWS Lambda function with an Amazon EFS event source to process the files.

- B: Send the JSON files to Amazon Elastic File System (Amazon EFS). Schedule an AWS Lambda function to process the files once each hour.

- C: Send the JSON files to an Amazon S3 bucket. Configure an AWS Lambda function with an S3 event source to process the S3 objects.

- D: Send the JSON files to an Amazon S3 bucket. Schedule an AWS Lambda function to process the S3 objects once each hour.

Notes.  Amazon EFS file system changes cannot invoke Lambda functions. Lambda functions can be scheduled.

Correct answer

- C: Send the JSON files to an Amazon S3 bucket. Configure an AWS Lambda function with an S3 event source to process the S3 objects.

    Lambda functions can be invoked from S3 events and can read from S3 buckets. An event-based invocation would allow for the S3 objects to be processed as soon as they arrive.

    For more information about invoking a Lambda function from S3, see Tutorial: Using an Amazon S3 trigger to invoke a Lambda function.

## 11

A developer needs to query a relational database from an AWS Lambda function. The Lambda function will be called frequently. The developer needs to avoid the latency introduced by the initial JDBC connection to the database in subsequent invocations of the Lambda function.

How can the developer ensure the database connection is reused by Lambda?

- A: Initialize the database connection outside the Lambda function code as a Lambda function environment variable.

- B: Initialize the database connection within the Lambda function code but outside the handler method.

- C: Store the database connection string in AWS Systems Manager Parameter Store. Ensure the Lambda function handler initializes the database connection within the handler method.

- D: Store the database connection string in the Lambda function code. Ensure the function handler initializes the database connection within the handler method.

Correct answer

- B: Initialize the database connection within the Lambda function code but outside the handler method.

    The Lambda environment can reuse the same database connection for subsequent invocations when defining the database connection details in the code but outside the handler method.

    For more information about reusing the Lambda execution environment, see AWS Lambda execution environment.

## 12

An ecommerce company deploys more than 20 services behind Amazon API Gateway. The interaction between services is complex. Each service can potentially call several others, making performance issues and errors difficult to identify. Some individual API calls have experienced slow response times. The development team needs to quickly identify the underlying causes of the slowdowns.

Which approach would MOST quickly identify the underlying cause of performance issues?

- A: Use Amazon CloudWatch metrics to find the service invocations with slow response times. Configure and use AWS X-Ray to examine these services to discover their performance issues.

- B: Use AWS CloudWatch Logs to find the service invocations with slow response times. Use AWS CloudTrail to examine these services to discover their performance issues.

- C: Configure and use AWS X-Ray to find the service invocations with slow response times. Use Amazon CloudWatch metrics and logs to examine these services to discover their performance issues.

- D: Use AWS CloudTrail to find the service invocations with slow response times. Configure and use AWS X-Ray to examine these services to discover their performance issues.

### Incorrect answers

- A: Use Amazon CloudWatch metrics to find the service invocations with slow response times. Configure and use AWS X-Ray to examine these services to discover their performance issues.

    Incorrect. It is time consuming to examine and compare metric values of various services. The number of CPU or network calls a service makes indicates relative work load. The number of these CPU or network calls does not indicate poor performance. X-Ray is mainly used to study a service's interaction time with other services. It has limited utility to diagnose an individual service's performance. However, X-Ray is excellent at quickly finding poorly performing services within a web of interaction. CloudWatch metrics and logs can be used to study the targeted services.

- B: Use AWS CloudWatch Logs to find the service invocations with slow response times. Use AWS CloudTrail to examine these services to discover their performance issues.

    Incorrect. Not all services send logs to CloudWatch Logs. It is time consuming to examine a large numbers of different log files. Log output is application-specific and may not provide any insight into performance issues. CloudTrail records API calls, not application-level activity.

    For more information about CloudTrail, see What is AWS CloudTrail?

- D: Use AWS CloudTrail to find the service invocations with slow response times. Configure and use AWS X-Ray to examine these services to discover their performance issues.

    Incorrect. CloudTrail records API calls. CloudTrail is not an application log aggregator, such as CloudWatch Logs. Any API calls that individual services make would be not be likely to affect application performance. Also, X-Ray is mainly used to study a service's interaction time with other services. It has limited utility to diagnose an individual service's performance.

Correct answer

- C: Configure and use AWS X-Ray to find the service invocations with slow response times. Use Amazon CloudWatch metrics and logs to examine these services to discover their performance issues.

    Correct. Unlike metrics or logs, X-Ray can help users quickly identify services by their relative response times. X-Ray can identify a poorly performing service from within a web of interacting services. Once identified, CloudWatch provides the context, including the logs and metrics necessary to study specific issues.

## 13

## 14

## 15

## 16

## 17

## 18

## 19

## 20
