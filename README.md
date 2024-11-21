AWS Project: Blog Generator
This project demonstrates the use of AWS Bedrock, S3, Lambda, API Gateway, and CloudWatch to create a blog generator. The system accepts a topic, generates a blog using the AWS Bedrock Meta Llama 3.2 70B Vision Instruct Model, and saves the blog as a .txt file in an S3 bucket. It also provides logs in AWS CloudWatch for monitoring.

Table of Contents
Overview
Architecture
Technologies Used
Setup Steps
1. AWS Bedrock Access
2. S3 Bucket Creation
3. Lambda Function Setup
4. API Gateway Setup
5. Postman Testing
Usage
License
Overview
This project uses the following AWS services:

AWS Bedrock: To generate blogs using the Meta Llama 3.2 70B Vision Instruct Model.
AWS S3: To store the generated blog as a .txt file.
AWS Lambda: For serverless execution of the blog generation logic.
API Gateway: To expose an HTTP endpoint for blog generation.
CloudWatch: To monitor and debug the system.
Architecture
A POST request is sent to the API Gateway with a topic.
The request triggers a Lambda function, which generates a blog using the AWS Bedrock Meta Llama model.
The generated blog is saved to an S3 bucket.
Logs and execution details are available in CloudWatch.
Technologies Used
Python (Lambda Function)
AWS Services:
Bedrock
S3
Lambda
API Gateway
CloudWatch
Postman (for API testing)
Boto3 (Python AWS SDK)
Setup Steps
1. AWS Bedrock Access
Request access to AWS Bedrock.
Once granted, switch to the North East Virginia (us-east-1) region.
Use the Meta Llama 3.2 70B Vision Instruct Model with the following model ID:
text
Copy code
meta.llama3-70b-instruct-v1:0  
2. S3 Bucket Creation
Create an S3 bucket named awsbedrockcourse1.1.
The generated blog will be saved as output-blog.txt in this bucket.
3. Lambda Function Setup
Create a Lambda function named awsbedrockapi.
Set the runtime to Python 3.13/3.12/3.11.
Write and deploy the blog generation code in the Lambda function.
Add Boto3 Library:
Since AWS Lambda doesn't include the latest boto3 library by default, create a layer:
Zip the boto3 library and upload it to a Lambda layer named boto3updatedlayer.
Attach this layer to your Lambda function.
Assign Administrator Access to the Lambda function in the IAM policy.
4. API Gateway Setup
Create an API Gateway named bedrockldemoapi.
Add a POST route: /blog-generation.
Deploy the API to a stage named dev.
Copy the API URL.
5. Postman Testing
Open Postman and select POST.
Enter the URL:
arduino
Copy code
https://<your-api-id>.execute-api.us-east-1.amazonaws.com/dev/blog-generation  
In the request body, pass the blog topic as JSON:
json
Copy code
{  
   "blog_topic": "MS Dhoni"  
}  
Submit the request.
6. CloudWatch Logs
Open CloudWatch to monitor Lambda function execution logs.
Verify that the blog generation process was successful.
7. Check S3 Bucket
Go to the S3 bucket (awsbedrockcourse1.1).
Verify the presence of output-blog.txt containing the generated blog.
Usage
Clone the repository and follow the Setup Steps.
Use Postman or any API testing tool to test the API.
Monitor logs in CloudWatch for debugging.
License
This project is licensed under the MIT License.
