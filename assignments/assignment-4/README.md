# Assignment 4 — Serverless API with Lambda, API Gateway, and DynamoDB

## Overview
This assignment implements a **serverless REST API** using AWS services. The API allows clients to submit student data via a POST request, stores it in DynamoDB, and optionally retrieves all students with a GET request.  

The workflow demonstrates **API Gateway → Lambda → DynamoDB** integration, **CORS configuration**, **IAM least-privilege**, and **CloudWatch logging**.

---

## Architecture
The serverless architecture can be visualized as:

[View Architecture Diagram](YOUR_ARCHITECTURE_LINK_HERE)

**Flow:**
1. Client sends POST `/submit` → API Gateway  
2. API Gateway triggers Lambda function  
3. Lambda generates UUID, timestamp, and stores payload in DynamoDB  
4. Lambda returns a JSON response to the client  
5. Optional GET `/students` fetches all items from DynamoDB  

---

## Lambda Function
The Lambda function handles both POST and GET requests:

- **POST**:
  - Receives JSON payload
  - Generates a unique UUID
  - Adds a timestamp
  - Stores the item in the DynamoDB table `students`
  - Returns a success JSON response
- **GET** (optional):
  - Scans the DynamoDB table
  - Returns all stored student items

The function uses **Python 3.12 runtime** and follows **least-privilege IAM roles** — only allowing `PutItem` on DynamoDB and logging permissions for CloudWatch.

The lambda code that was used is here: [lambda-code-used](./lambda-code-used)

---

## What I Learned
- How to **create and configure DynamoDB tables** (partition keys, on-demand capacity)  
- How to **write Lambda functions** with Python and integrate with API Gateway  
- How to **enable CORS** and deploy APIs to stages  
- How to **use CloudWatch** to debug and verify Lambda executions  
- The importance of **IAM least-privilege** policies in real AWS environments  

---

## Challenges & Solutions
- **Missing Authentication Token**:  
  - Solved by ensuring the POST request included `/submit` in the URL and deploying the correct stage
- **CORS issues**:  
  - Fixed by enabling CORS for the `/submit` resource in API Gateway
- **Lambda debugging**:  
  - Added `print()` statements for payloads and responses to verify execution in CloudWatch
- **GET endpoint errors**:  
  - Solved by safely checking `event.get("httpMethod")` to prevent runtime errors

---

## Verification & Documentation
Everything has been **documented with screenshots** to demonstrate functionality and configuration:

- DynamoDB table overview and items  
- Lambda configuration  
- POST request results (terminal / curl)  
- CloudWatch logs  
- API Gateway resources, POST → Lambda integration, and deployment  

[Check all screenshots here](YOUR_SCREENSHOTS_LINK_HERE)

---

## Summary
This assignment demonstrates the **end-to-end deployment of a serverless API** on AWS.  
All components have been **verified and documented**, and the Lambda function is fully functional for both POST and optional GET operations.  

The repository contains:  
- Lambda function code  
- Screenshots of all relevant configurations  
- Architecture diagram  
- README detailing workflow, learning points, and challenges  

