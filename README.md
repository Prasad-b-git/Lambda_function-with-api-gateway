# AWS Contact Form Project

A serverless contact form solution built with AWS services including API Gateway, Lambda, and DynamoDB.

![Architecture Diagram](arc.jpg)

## Project Overview

This project implements a modern, responsive contact form that stores user submissions in a DynamoDB database through a serverless architecture. The solution uses AWS Lambda for backend processing and API Gateway for secure API access.

## Features

- Modern, responsive contact form with gradient styling
- Serverless backend processing with AWS Lambda
- Data persistence using Amazon DynamoDB
- Secure API access with API Gateway and API key authentication
- Form validation and user feedback
- Animated UI elements for better user experience
- Cross-browser compatibility

## Architecture

The solution uses the following AWS services:

1. **Amazon S3**: Hosts the static website files (HTML, CSS, JavaScript)
2. **Amazon API Gateway**: Provides secure API endpoints with API key authentication
3. **AWS Lambda**: Processes form submissions and interacts with DynamoDB
4. **Amazon DynamoDB**: Stores contact form submissions
5. **IAM**: Manages permissions between services

## Setup Instructions

### Prerequisites
- AWS Account
- AWS CLI configured with appropriate permissions
- Basic knowledge of AWS services

### Deployment Steps

#### 1. DynamoDB Setup
1. Create a DynamoDB table named `Users` with a primary key of your choice (e.g., `email`)

#### 2. Lambda Function Setup
1. Create a new Lambda function
2. Upload the provided Lambda code (`lambda_function.py`)
3. Set environment variables:
   - `DYNAMODB_TABLE`: Name of your DynamoDB table (default is "Users")
4. Add the following permissions to the Lambda execution role:
   - `AmazonDynamoDBFullAccess` (or a more restrictive custom policy)

#### 3. API Gateway Setup
1. Create a new REST API
2. Create a resource and configure methods:
   - `GET`: To retrieve the contact form
   - `POST`: To submit form data
   - `OPTIONS`: For CORS support
3. Enable API key requirement for the methods
4. Create a new API key and associate it with your API
5. Deploy the API to a stage (e.g., "dev" or "prod")
6. Enable CORS for the API

#### 4. Frontend Setup
1. Update the API endpoint URL and API key in the HTML file:
   ```javascript
   const API_ENDPOINT = 'YOUR_API_GATEWAY_URL';
   const API_KEY = 'YOUR_API_KEY';
   ```
2. Upload the HTML file to an S3 bucket configured for static website hosting or your preferred hosting service

### Configuration Files

The project includes the following files:

- `contactus.html`: The main contact form HTML file
- `success.html`: Success page displayed after form submission
- `lambda_function.py`: AWS Lambda function code
- `arc.jpg`: Architecture diagram of the solution

## Usage

1. Access the contact form through your deployed URL
2. Fill out the form with your information
3. Submit the form
4. Upon successful submission, you'll be redirected to a success page
5. Form data will be stored in the DynamoDB table

## Security Considerations

- API key authentication is implemented to secure the API endpoints
- CORS headers are properly configured to allow requests only from authorized domains
- Form data is validated on both client and server sides
- Error handling is implemented to prevent exposure of sensitive information

## Customization

You can customize the following aspects of the project:

- UI colors and styles by modifying the CSS variables in the HTML file
- Form fields by adding or removing input elements in the HTML
- Backend processing logic by modifying the Lambda function
- Database schema by adjusting the DynamoDB table structure

## Troubleshooting

### Common Issues

1. **Form submission fails**:
   - Verify that the API key is correct
   - Check that CORS is properly configured
   - Ensure the Lambda function has the necessary permissions

2. **Lambda function errors**:
   - Check CloudWatch Logs for error details
   - Verify that the DynamoDB table exists and is accessible

3. **API Gateway issues**:
   - Ensure the API is properly deployed to a stage
   - Verify that the API key requirement is configured correctly

## Project by

Prasad Bandagale

## License

[Specify your license here]
