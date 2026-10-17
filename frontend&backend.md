# Build and Deploy Frontend Application Using S3 and CloudFront 

## Create S3 Bucket for Frontend
![S3 Bucket](images/11.png)


## Create cloud front distribution:
![S3 Bucket](images/12.png)

# Configure and Build React Application and Deploy to S3
1.	Navigate to frontend directory:
    ``` cd frontend/react-app ```
2. 	Edit src/aws-config.js:
```   const awsConfig = {
  Auth: {
    Cognito: {
      userPoolId: '<COGNITO_USER_POOL_ID>',       // e.g., ap-south-1_xxxxxxxxx
      userPoolClientId: '<COGNITO_CLIENT_ID>',    // e.g., 1a2b3c4d5e6f7g8h9i0j1k2l3m
      loginWith: {
        email: true,
      },
    }
  },
  API: {
    baseUrl: ''  // Leave empty for now — will be updated in Module 7
  }
};

export default awsConfig;
```


## Build and Deploy React frontend
### 3.	Install dependencies:
``` npm install ```
### 4.	Build:
``` npm run build ```
### 5.	Deploy frontend build to S3:
``` aws s3 sync build/ s3://<your-frontend-bucket-name> --delete --exclude "images/*" ```


![S3 Bucket](images/13.png)
![S3 Bucket](images/14.png)

## Upload Product Images to S3 bucket

``` cd data ```


``` bash upload-images-to-s3.sh <your-bucket-name>  ```



![S3 Bucket](images/15.png)

## Add/upload data to S3 and DynamoDB

### Create Dynamodb table for product and cart service
![S3 Bucket](images/16.png)


### Update Product Image URLs

``` # Run from the repo root directory ```
``` cd data ```
``` bash update-product-image-urls.sh <cloudfront URL> ```

### Load Products into DynamoDB

``` bash load-products.sh <your-region> ```

### Create Amazon RDS Database

Create DB Subnet Group
![S3 Bucket](images/17.png)

Create Security Group for RDS
![S3 Bucket](images/18.png)

### Create rds database
![S3 Bucket](images/19.png)


## Parameter Store - Configuration Management

![S3 Bucket](images/20.png)

## Create Application Load Balancer (internal)

![S3 Bucket](images/21.png)

Create Target Groups
![S3 Bucket](images/22.png)

## Create load balancer

Configure ALB Listener Rules

![S3 Bucket](images/23.png)

## Create ECR Repositories

![S3 Bucket](images/24.png)

## Create IAM Role for ECS Tasks

![S3 Bucket](images/25.png)

## Create ECS Security Group
![S3 Bucket](images/26.png)

## Create ECS Task Definitions
![S3 Bucket](images/27.png)

## Create ECS Cluster and Services

![S3 Bucket](images/28.png)

## Create VPC Link
Create Security Group for VPC Link
![S3 Bucket](images/29.png)
![S3 Bucket](images/30.png)

## Create HTTP API Gateway
![S3 Bucket](images/31.png)


## Create HTTP Integration

![S3 Bucket](images/32.png)

## Create Cognito JWT Authorizer

![S3 Bucket](images/33.png)

## Create API Routes
![S3 Bucket](images/34.png)

## Configure CORS

![S3 Bucket](images/35.png)

## Update frontend with API Gateway URL
### 1.	Navigate to frontend directory:
```cd frontend/react-app ```
### 2.	Edit src/aws-config.js — update only the baseUrl field:
```const awsConfig = {
  Auth: {
    Cognito: {
      userPoolId: '<COGNITO_USER_POOL_ID>',       // Already set in Module 3
      userPoolClientId: '<COGNITO_CLIENT_ID>',    // Already set in Module 3
      loginWith: {
        email: true,
      },
    }
  },
  API: {
    baseUrl: '<API_GATEWAY_URL>'  // e.g., https://xxxxxxxxxx.execute-api.us-east-1.amazonaws.com
  }
};

export default awsConfig;```


```
### Rebuild and redeploy frontend to S3

```
npm run build
aws s3 sync build/ s3://<your-frontend-bucket-name> --delete --exclude "images/*"


```

![S3 Bucket](images/36.png)

## Create SNS Topic
![S3 Bucket](images/37.png)

## Create SQS Queue for Logging
![S3 Bucket](images/38.png)

## Configure SNS Subscriptions

![S3 Bucket](images/39.png)

SQS Subscription for Shipping

![S3 Bucket](images/40.png)

![S3 Bucket](images/41.png)







