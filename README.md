## Amazon SQS Java Temporary Queues Client

An Amazon SQS client that supports creating lightweight, automatically-deleted temporary queues, for use in common messaging patterns such as Request/Response.

This library provides two complimentary interfaces for two-way communication through queues:

* an `AmazonSQSRequester` [interface](./src/main/java/com/amazonaws/services/sqs/AmazonSQSRequester.java)
enabling message producers to send a message and wait for a corresponding response message, and 
* an `AmazonSQSResponder` 
[interface](./src/main/java/com/amazonaws/services/sqs/AmazonSQSResponder.java)
enabling message consumers to send response messages.

To implement this pattern efficiently, the `AmazonSQSRequester` client creates internal temporary queues to hold response messages. The temporary queues architecture scales
to an arbitrary number of message producer runtimes, with no danger of response messages being consumed by the wrong client.
The temporary queues are also guaranteed to be automatically deleted if the clients that created them die ungracefully!
By default, these internal queues are created with the queue name prefix `"__RequesterClientQueues__"`, but this can be customized when 
[building](./src/main/java/com/amazonaws/services/sqs/AmazonSQSRequesterClientBuilder.java)
the requester client.

This library is currently in developer preview and we look forward to community feedback and collaboration! The internal components used to implement the
Request/Response interfaces have other applications, and we plan to make more of them accessible for other use cases in the future.

## Getting Started

* **Sign up for AWS** -- Before you begin, you need an AWS account. For more information about creating an AWS account and retrieving your AWS credentials, see [AWS Account and Credentials](http://docs.aws.amazon.com/AWSSdkDocsJava/latest/DeveloperGuide/java-dg-setup.html) in the AWS SDK for Java Developer Guide.
* **Sign up for Amazon SQS** -- Go to the Amazon [SQS console](https://console.aws.amazon.com/sqs/home?region=us-east-1) to sign up for the service.
* **Minimum requirements** -- To use this client, you'll need Java 8 (or later) and [Maven 3](http://maven.apache.org/).
* **Download** -- Download the [latest preview release](https://github.com/awslabs/amazon-sqs-java-temporary-queues-client/releases) or pick it up from Maven:
```xml
  <dependency>
    <groupId>com.amazonaws</groupId>
    <artifactId>amazon-sqs-java-temporary-queues-client</artifactId>
    <version>0.9.1</version>
    <type>jar</type>
  </dependency>
```
* **Samples** -- Sample code using this library is available [here](https://github.com/aws-samples/amazon-sqs-java-temporary-queues-client-samples).
* **Further information** - Read the [API documentation](http://aws.amazon.com/documentation/sqs/).

## Feedback
* Give us feedback [here](https://github.com/awslabs/amazon-sqs-java-temporary-queues-client/issues).
* If you'd like to contribute a new feature or bug fix, we'd love to see Github pull requests from you!

## License

This library is licensed under the Apache 2.0 License. 

See [LICENSE](./LICENSE) and [NOTICE](./NOTICE) for more information.