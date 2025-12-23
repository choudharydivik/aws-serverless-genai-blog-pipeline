# aws-serverless-genai-blog-pipeline
## End-to-End Serverless GenAI Flow (Using AWS Bedrock,Lambda)

```text
ARCHITECTURE
------------
Postman / Client
        |
        v
+--------------------+
|   API Gateway      |
|  (HTTP Trigger)    |
+--------------------+
        |
        v
+-------------------------------+
|        AWS Lambda             |
|  - Parse request              |
|  - Call Bedrock               |
|  - Store output in S3         |
+-------------------------------+
      |                  |
      v                  v
+---------------+   +-------------------+
| Amazon        |   | Amazon S3         |
| Bedrock       |   | (Blog Storage)    |
| (LLM Inference)|  |                   |
+---------------+   +-------------------+

WORKFLOW
--------
1. Client sends a blog topic via HTTP POST request
2. API Gateway triggers the AWS Lambda function
3. Lambda invokes Amazon Bedrock to generate the blog
4. Generated blog is stored in an Amazon S3 bucket
5. API returns a success response

AWS SERVICES USED
-----------------
- Amazon API Gateway  → HTTP trigger for Lambda
- AWS Lambda          → Core business logic execution
- Amazon Bedrock      → Blog generation using LLM
- Amazon S3           → Storage for generated blog files
- IAM Roles           → Secure access between services
