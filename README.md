# ServerLess-Image-Rekog
This project is a serverless image recognition application built using AWS services. It automatically analyzes images uploaded to an S3 bucket using Amazon Rekognition and checks for specific labels. Based on the labels detected, the images are categorized into success or failure folders. The system uses SQS to queue image analysis requests, Lambda for processing logic, and CloudWatch for monitoring and logging. It ensures secure, scalable, and automated image classification with integrated alerts through SNS for real-time notifications.

![image](https://github.com/user-attachments/assets/bc07e786-f035-46ec-ba42-7a9f38b037dd)


S3 Bucket Setup:
Bucket Name: widget-inspection-images
Folders: /images (input), /analyzed (subfolders: /success, /failure)
Event Notification: Trigger SQS on PUT events for image uploads
SQS Queue Setup:
Queue Name: image-analysis-queue
Access Policy: Grant S3 permission to publish to the queue
Dead-Letter Queue: image-analysis-dlq for failed messages
AWS Rekognition:
Purpose: Detect specific labels (e.g., "Football", "Widget") in images
Integration: Lambda function invokes Rekognition to analyze S3 images
Lambda Function Setup:
Role: Analyzes images, categorizes, and moves them to /success or /failure
Permissions: S3 (read/write), Rekognition (read), CloudWatch (logs), SQS (read)
![image](https://github.com/user-attachments/assets/2005f6ae-55a5-44db-ab37-9dd87179a698)

![image](https://github.com/user-attachments/assets/9fc3b3c4-ed34-4a14-9ede-873c65fab123)
