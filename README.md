# Deploy Static Website on AWS

In this project, a static website is deployed to AWS using S3, CloudFront, and IAM.

![Website Homepage](docs/images/website-homepage.png)

**Live Demo:** [GitHub Pages](https://sasa94s.github.io/deploy-a-static-website-on-aws) | [AWS CloudFront](https://d39g58ktisuizc.cloudfront.net) | [AWS S3 Bucket](https://melsheikh-travel-blog.s3.amazonaws.com/index.html)

**Note:** Website can be accessed through AWS with limited access. (29/11/2021)

## Table of Content
1. [Project Structure](#project-structure)
2. [Access Website in Web Browser](#access-website-in-web-browser)
3. [Getting Started](#getting-started)
   1. [Create S3 Bucket](#create-s3-bucket)
   2. [Upload files to S3 bucket](#upload-files-to-s3-bucket)
   3. [Secure Bucket via IAM](#secure-bucket-via-iam)
   4. [Configure S3 Bucket](#configure-s3-bucket)
   5. [Distribute Website via CloudFront](#distribute-website-via-cloudfront)

## Project Structure

| Project Item | Description                                                                                 |
|--------------|---------------------------------------------------------------------------------------------|
| index.html   | The Index document for the website.                                                         |
| /img         | The background image file for the website.                                                  |
| /vendor      | Bootssrap CSS framework, Font, and JavaScript libraries needed for the website to function. |
| /css         | CSS files for the website.                                                                  |

## Access Website in Web Browser

There are three ways to access the bucket:

|Source|URL|Screenshot
|---|---|---
|CloudFront|https://d39g58ktisuizc.cloudfront.net|[Click to view](docs/images/web-home-cloudfront.png)
|Website Endpoint|http://melsheikh-travel-blog.s3-website.us-east-1.amazonaws.com/|[Click to view](docs/images/web-home-endpoint.png)
|S3 Object URL|https://melsheikh-travel-blog.s3.amazonaws.com/index.html|[Click to view](docs/images/web-home-s3.png)

## Getting Started

### Create S3 Bucket
1. Go to Amazon S3
2. Click on "Create Bucket"
3. Specify Bucket Name, e.g. "melsheikh-travel-blog"
![S3 - Create Bucket](docs/images/s3-createbucket.png)
4. Allow Public Access to the Bucket
   1. Uncheck "Block all public access"
   2. Check "I acknowledge that the current settings might result in this bucket..."
   ![S3 - Public Access](docs/images/s3-publicaccess.png)

### Upload files to S3 bucket
1. Click on "Upload files"
2. Click on "Add files" to select "index.html"
3. Click on "Add folders" to select "css", "img", and "vendor"
4. Check selected files and proceed to upload
![S3 - Upload](docs/images/s3-upload.png)

### Secure Bucket via IAM
1. Click on "Permissions" tab
2. Click on "Edit" button in "Bucket policy"
3. Copy content of [bucketPolicy.json](docs/bucketPolicy.json) and paste it
4. Click on "Save"
![S3 - Permissions](docs/images/s3-permissions.png)

### Configure S3 Bucket
1. Click on "Properties" tab
2. Click on "Edit" button in "Static website hosting"
3. Select "Enabled" option
4. Specify index document "index.html"
5. Click on "Save changes"
![S3 - Static Website Hosting](docs/images/s3-staticwebhosting.png)
6. Check Bucket's Public Web URL provided under the section
![S3 - Public Bucket Web URL](docs/images/s3-publicbucketurl.png)

### Distribute Website via CloudFront
1. Go to Amazon CloudFront
2. Click on "Create a CloudFront distribution"
3. Choose S3 Bucket Origin Domain
4. Select "Yes use OAI"
![CloudFront - Create Distribution](docs/images/cloudfront-createdistribution.png)
5. Click on "Create new OAI"
6. Click on "Create" to proceed
![CloudFront - Create new OAI](docs/images/cloudfront-createnewoai.png)
7. Select "Yes, update Bucket policy"
8. Include "Default root object" as "index.html"
9. Leave others as defaults
![CloudFront - Distribution](docs/images/cloudfront-distribution.png)
