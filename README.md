# AWS Serverless Contact Routing

## Overview

This project demonstrates a simple event-driven serverless architecture on AWS.

The application exposes an API for collecting user contacts and routes requests through AWS messaging services before persisting data into DynamoDB.

The purpose of this repository is architectural and educational rather than production-oriented.


The system:

- Receives the request through API Gateway
- Invokes a Lambda function
- Publishes an event to SNS
- Routes the event to the appropriate SQS queue
- Invokes a worker Lambda
- Stores the contact in DynamoDB

AWS Services Used:
- Amazon API Gateway
- AWS Lambda
- Amazon SNS
- Amazon SQS
- Amazon DynamoDB

ARCH FLOW:
- Client
- API Gateway
- Lambda Ingress
- SNS Topic -->  SQS ITA  or  SQS FOREIGN
- Lambda Worker
- DynamoDB
--

## Architecture

![Architecture](architecture.png)

---

## Use Case

A client submits:

```json
{
  "name": "Mario Rossi",
  "phone": "+39333111222"
}

