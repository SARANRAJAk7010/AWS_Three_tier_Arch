# AWS_Three_tier_Arch
Three Tier Architecture
- Presentation layer
- Logic tier
- Data tier

 
1. --> Website Delivery with CloudFront <-- (Presenation tier)



In this Project: 
- create a storage space in S3 for your website's files.
- Set up CloudFront to distribute your website globally.
- Manage permissions for both S3 and CloudFront.
- Compare different methods for hosting your website and analyze their performance.

Presentation tier --> Setup(html, css, js) -> s3 bucket -> CloudFront distribution -> Output(distributed website).

Step 1: Set Up an S3 Bucket
s3 console -> create bucket -> bucket name -> create

Step 2: Upload Website Files
s3 console -> Upload 3 files(html,css,js)

Step 3: Set Up a CloudFront Distribution
CloudFront console -> Select Create a CloudFront distribution -> Distribution name -> Distribution type, select the Single website or app option -> Origin panel, select the Browse S3 button -> Web Application Firewall (WAF), select Do not enable security protections -> Create distribution.

Step 4: Verify your CloudFront Distribution
Copy the distribution domain name -> Paste it on browser -> Error "site cant be reached".

Step 5: Update your CloudFront settings
CloudFront console -> Origins -> se;ect your bucket -> Change the setting from Public to Origin access control settings -> new Origin access control heading, select Create new OAC -> 

Step 6: Update your S3 bucket's settings
CloudFront distribution's settings page, select Copy policy -> S3 bucket's Permissions tab -> Bucket policy section -> paste -> save -> Check url NOw its working.



2. --> APIs with Lambda + API Gateway <--  (LOgic tier)

In this project,
- Develop a serverless Lambda function.
- Configure an API with API Gateway.
- Connect Lambda with API Gateway.
- Write JSON documentation for your API.

Logic Tier :  User -> API Gateway (GET Method) -> Lambda

Step 1: Create a Lambda Function.
Lambda console -> create a function -> Author from scratch -> enter func name -> Runtime, Node.js -> Architecture, x86_64 -> create Function -> Down to the Code source panel -> copy and paste code -> deploy.

Step 2: Set up API Gateway.
API Gateway console -> list of APIs -> REST API -> Build -> API details, New API -> API name -- API endpoint type, Regional -> create API.

Step 3: Set up an API Resource. 
Resources, Create resource -> name 'users' -> Create resource -> Select /users resource.

Step 4: Set up an API Method. (GET, POST, PUT, DELETE)
Methods panel, Create method -> GET from Methodtype dropdown -> Lambda Function for the Integration type -> Switch on Lambda proxy integration -> select RetrieveUserData function -> create method.

Step 5: Deploy your API
Select Deploy API -> Stage, New stage -> Stage name, prod -> select deploy
Find invoke URL & check.


3. --> Fetch Data with AWS Lambda <--  (data tier)

In this project,
- Create a database table to store user data.
- Create a serverless function to retrieve user data.
- Write tests to validate if your function can fetch data from DynamoDB.
- Secure your serverless function with proper permissions.
- Secure your database with an inline policy

(Setup) DynamoDB table -> Add table items -> Lambda func -> Add func code --> (Test) test Lanmba func --> (Troubleshoting) Update Lambdas IAM role --> (Output) Lambda func retreice data.

Step 1: Set up DynamoDB
Dynamo DB console -> Create table -> Table name, UserData -> Partition key, userId -> 'String' as partition type -> Create table.

Step 2: Add a Table Item
select UserData table -> Explore table items -> Create item -> Select 'Switch to JSON view' -> Toggle off 'View DynamoDB JSON' -> paste below 
{
  "userId": "1",
  "name": "Test User",
  "email": "test@example.com"
}
-> create item.

Step 3: Create the Lambda Function
Lambda service -> create func -> Author fromm Scratch -> Func name, RetrieveUserData -> Runtime, Node.js -> Expand the Change default execution role arrow -> Keep Create a new role with basic Lambda permissions -> Create Function.

Step 4: Implement the Lambda Function Logic
Lambda code editor -> copy & paste the code -> Deploy

Step 5: Write a Lambda Function Test
Still in the Lambda func, Test tab -> Event JSON panel, paste below-> 
{
  "userId": "1"
}

Step 6: Grant DynamoDB Access to Lambda
switch configuration tab in lambda func -> Permissions -> select execution role like retreiveUSeXXXXXXXX -> Add Permissions -> Attach Policies -> Type DynamoDB -> select AmazonDynamoDBReadOnlyAccess -> Add permissions.







