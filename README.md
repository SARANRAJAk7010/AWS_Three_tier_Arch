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



