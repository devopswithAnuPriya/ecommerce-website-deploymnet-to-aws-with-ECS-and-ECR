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
