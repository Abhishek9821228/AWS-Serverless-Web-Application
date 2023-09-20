# Serverless Web Application

## Overview
The application will present users with an HTML-based user interface for indicating the location where they would like to be picked up and will interact with a RESTful web service on the backend to submit the request and dispatch a nearby unicorn. 
The application will also provide facilities for users to register with the service and log in before requesting rides.


## Architecture

The application architecture uses AWS Lambda, Amazon API Gateway, Amazon DynamoDB, Amazon Cognito, and AWS Amplify Console. Amplify Console provides continuous deployment and hosting of the static web resources including HTML, CSS, JavaScript, and image files which are loaded in the user's browser. JavaScript executed in the browser sends and receives data from a public backend API built using Lambda and API Gateway. Amazon Cognito provides user management and authentication functions to secure the backend API. Finally, DynamoDB provides a persistence layer where data can be stored by the API's Lambda function.

AWS services used

- Amplify
- Lambda
- API Gateway
- DynamoDB
- Cognito
- IAM

![App Screenshot](https://d1.awsstatic.com/diagrams/Serverless_Architecture.d930970c77b382db6e0395198aacccd8a27fefb7.png)

# Step 1 - Hosting a static Website using AWS amplify and Codecommit

In this step, I used AWS codecommit as a version control service.

    1. create a codecommit repo. 
    2. Creating IAM user for HTTP connection to out aws repo. 
    3. using AWS Access Key ID and Secret Access Key to configure AWS CLI.
    4. Set up git helper credentials.
    5. Clone the codecommit repo locally.
    6. Now populate the empty repo by downloading file from AWS s3.
    7. Now enable the web hosting using Amplify.
    8. Use the hosting option with codecommit and deploy it. 

![App Screenshot](https://d1.awsstatic.com/diagrams/wildrydes_clone2.e6d9848ab994e802888144e31d777999631d0758.png)

    9. The website will be shown one deployed.


In this step we completed the website hosting using codecommit and Amplify.

![App Screenshot](https://d1.awsstatic.com/diagrams/Amplify_Wild_Rydes.1760839c5336d01cd6ac6eabb5d2ad8a37c3304a.png)


# Step 2 - Setting up the AWS Cognito for user authentication.

In this step, I created an Amazon Cognito user pool to manage your users' accounts. I deployed pages that enable customers to register as a new user, verify their email address, and sign into the site.

    1. Create a user pool.
    2. We can create user pool or idenetiy pool, I used user pool with email and passowrd verification.
    3. I used AWS SES service to send mails to verify emails.
    4. After creating the user pool, We need to the client Id and user pool Id.
    5. We can use these 2 ID to create authentication.
    6. After implementing the cognito functionality, validate the process by creating a user.


![App Screenshot](https://d1.awsstatic.com/Test%20Images/Kate%20Test%20Images/Serverless_Web_App_LP_assets-03.1403870f0fabeb6a11d3e4116092aa6b19b6a924.png)


# Step 3 - Creating serverless backend using Lambda and DynamoDB.

In this step, I use AWS Lambda and Amazon DynamoDB to build a backend process for handling requests for web application. 

    1. Create a DynamoDB table, Make a partition key name "rideId".
    2. Save the ARN of the table, because it will be used later to add it with lambda.
    3. Now create a role for the lambda fucntion. Becuase the role define what other service the lambda function is allowed to interact with.
    4. Give AWSLambdaBasicExecutionRole  policy to role and also add DynamoDB putitem policy to this role.
    5. Now create a lambda function that gets trigged when a API call is made from frontend.


![App Screenshot](https://d1.awsstatic.com/Test%20Images/Kate%20Test%20Images/Serverless_Web_App_LP_assets_04.76030d61413ff43bd6aa75fbd16e02ad23aec67a.png)


# Step 4 - Creating API Gateway.

In this step, I use Amazon API Gateway to expose the Lambda function I built in the previous module as a RESTful API. This API will be accessible on the public Internet. It will be secured using the Amazon Cognito user pool you created in the previous module. 

    1. Create a new RESTful API.
    2. Now use Amazon Cognito User Pools to create a Amazon Cognito User Pools Autherizor.
    3. Now create a resource and a post method.
    4. Select Lambda Function for the Integration type.
    5. Now reploy the API.
    6. Now a url will be genrated which will be the url to invoke the lambda function.
    7. Its done and a serverless web Application has been created.



![App Screenshot](https://d1.awsstatic.com/Test%20Images/Kate%20Test%20Images/Serverless_Web_App_LP_assets_05.d1ecdfaab160d7dc00ddbc9e0245fa34b8d8f26b.png)
