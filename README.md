# How to deploy React/Vue based webapp to AWS using S3 & CloudFront

# What is CloudFront:
CloudFront is a Content Delivery Service that delivers content, yes who could have put those two together, such as videos, pictures, or applications to users. CloudFront will cache content to AWS Edge locations, providing faster retrieval time for users after the first initial retrieval. CloudFront is a global service and provides access to the backbone of the AWS network so that content is more easily served globally. For more information click the link AWS CloudFront.

# What is S3:

Amazon S3 (Simple Storage Service) provides object storage, which is built for storing and recovering any amount of information or data from anywhere over the internet. It provides this storage through a web services interface. While designed for developers for easier web-scale computing, it provides 99.999999999 percent durability and 99.99 percent availability of objects. It can also store computer files up to 5 terabytes in size.

Apart from data storage functionality, the AWS S3 bucket provides a remarkable feature of static website hosting over it. A website that doesn’t involve server-side communication is called a static website.

# Purpose:

To provision, one S3 bucket with a Text script in it, and have CloudFront serve our content by using this bucket as the origin. CloudFront will use Edge Locations thus reducing latency for our users.


## Requirements:

1. AWS account
2. Experience with S3
3. Some Experience with CloudFront.

# Let’s start:

## Creating & setting up S3 bucket:

Login into your AWS account, head over to the search bar at the top and search for S3.

![aws1](https://user-images.githubusercontent.com/47071968/200566861-ad16589e-25df-49fd-b9fb-181f6904b812.png)

Inside of the S3 dashboard, click on “Create bucket”.


![aws2](https://user-images.githubusercontent.com/47071968/200567092-17fff871-384c-4476-b88c-ed7375a481f4.png)

Scroll to the bottom and click “Create bucket”.


![aws3](https://user-images.githubusercontent.com/47071968/200567204-8d358f3b-9e0a-4b87-b034-896aa2a0f3d5.jpeg)

Then edit the bucket policy like below image.


![aws4](https://user-images.githubusercontent.com/47071968/200567314-ae549c27-12c6-4bd8-9923-a37f90e3623b.png)


After creating the bucket, upload your website to the bucket by clicking on the bucket name. Once inside of your bucket on the “Objects” tab, click on the “Upload” button.


![aws5](https://user-images.githubusercontent.com/47071968/200567441-bfbc1eaf-045e-401a-bb4f-ec53d7260dc4.jpeg)


From here you can upload your files multiple ways. You can click “Add files”, “Add folder” or drag and drop your items. Once you’re done click “Upload”.

![aws6](https://user-images.githubusercontent.com/47071968/200567773-849260da-13f8-4299-8b1c-59237eb45d42.jpeg)

NB: Now go to the local code repository and run “npm run build” as it’s js based project(React/Vue)

![aws7](https://user-images.githubusercontent.com/47071968/200568018-432faef1-777e-478b-a8d1-9e312fcc59fd.png)

And upload the files from ./dist directory.


![aws8](https://user-images.githubusercontent.com/47071968/200568329-226afd40-3fcf-496f-ad2d-9b318574e154.png)

The next step is to grant permissions to your bucket.

To do that, head over to the “Permissions” tab of your bucket. Scroll down to the “Bucket policy” section and click on the “Edit” button.

Paste the below code from below link into the bucket policy:
https://github.com/tanvirewu/s3_bucket_policy/blob/master/bucket_policy

### Setting up cloudfront:

To Setup a CloudFront distribution go to “CloudFront” from the AWS console and follow these steps:


![aws9](https://user-images.githubusercontent.com/47071968/200569085-d900e733-6cc9-4ef5-a766-56cd9bc4a0dc.png)

Click “Create distribution” and choose or enter your origin’s domain name.Set the origin domain name to be the newly created s3 bucket.

Set the default root object to index.html so it redirects / to /index.html



![aws10](https://user-images.githubusercontent.com/47071968/200569444-84788ce2-8f94-488e-905b-48915fec92d3.png)

Choose origin access and select Origin access control settings (recommended) and update the s3 bucket policy.


![aws11](https://user-images.githubusercontent.com/47071968/200569584-80d02043-db34-4140-97e6-134ba7b28c02.png)


Click Create Distribution and wait until the distribution is created.

Now let’s create invalidation under the “invalidation” section.


![aws12](https://user-images.githubusercontent.com/47071968/200569708-10e09652-73b3-43a5-a332-cd9f13b5e646.png)

Now,your website should be now accessible via the CloudFront distribution’s URL.

![aws13](https://user-images.githubusercontent.com/47071968/200569843-f72c35dc-5cf8-4c38-9c68-5d85ed3bdcec.png)


And if everything is set up correctly, you should be able to see a webpage like this!

![aws15](https://user-images.githubusercontent.com/47071968/200569983-d7fdde91-b181-48d3-b728-7ec9a0c2cc5d.png)

Thank you for reading.

Regards,

Md. Samdany Haque. 
