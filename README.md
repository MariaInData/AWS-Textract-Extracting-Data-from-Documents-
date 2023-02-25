# AWS-Textract-Extracting-Data-from-Documents-

#!("https://user-images.githubusercontent.com/125685678/221339541-7b959437-df3d-4c30-b52d-eb51bc054018.png")
![textract screenshot](https://user-images.githubusercontent.com/125685678/221339789-1b73b261-ddff-4840-9aea-14f5f2868d08.jpg)
How to instantly read extracted text, tables, and forms from images and PDF files using AWS Textract
# Analyze Terms and Conditions of a Scanned Document using AWS Textract

## Setup Front End
The front end of the application contains the interface used to intrecta with the application. The application is developed using python flask and the same can be found in FrontEnd Folder. Use the main.py to start the application. Get security keys from AWS S3 and replace thme in the application.

## AWS LAMBDA Back End 
The AWS Lambda conatins the code of LAMBDA functions.

Steps to implement the demo:

First we create an S3 bucket where we create the following folders: - Files: Where we add our template and the filled form which we want to compare - Textract Output: This is where the log files are stored once our textract operation runs - CSV: Where our output gets stored - Templates: Where our template gets stored

After this, we create and grant permissions for accepting and running the operation on the files. This is done through IAM - where we create the following roles: - AWSServiceRoleForSupport: The AWSServiceRoleForSupport service-linked role enables all AWS Support API calls to be visible to customers through AWS CloudTrail. This helps with monitoring and auditing requirements, because it provides a transparent way to understand the actions that AWS Support performs on your behalf.

We also use the SNS - Simple Notification Service for the textract-async-notification: With the help of this, as soon as the textract output is created, it sends a notification to AWS for the next steps to generate the output of the file with respect to the template.

Lambda Functions: 2 functions: - textract_sync_job_creation: To create an job once we upload the file to the bucket. - textract-response-process: This is the function which scrapes the file and helps in finding the differences.

After this process has been completed - we simply upload the master file and after this upload the scanned document via the front end service. After clicking the submit button we get a document where the differences are hghlighted.

## Credits & Bibliography

AWS Textract Homepage - https://aws.amazon.com/textract/
Setup & Implementation - https://www.youtube.com/watch?v=L6vdd9OYF_8&t=2056s&ab_channel=SrceCde
Setup & Implementation - https://www.youtube.com/watch?v=IRmeekfUZeA&ab_channel=CloudGuru
AWS - https://docs.aws.amazon.com/managedservices/latest/userguide/textract.html
AWS - https://nanonets.com/blog/aws-textract-teardown-pros-cons-review/
