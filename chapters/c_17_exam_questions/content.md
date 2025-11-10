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