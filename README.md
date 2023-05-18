# AWS S3 Static Website Deployment using CLI

First open your command-line interface (CLI) and proceed with configuring your details using the following command:

***aws configure***

![1ss](https://github.com/harshartz/AWS-EC2/assets/130890384/4b5d8dac-c720-41d7-b25b-0d2326035073)


# Step 1: Create a Bucket

Use the following command to create a bucket:

***aws s3 mb s3://BUCKET-NAME***

Replace (BUCKET-NAME) with a globally unique name for your bucket. Make sure it is unique across all existing buckets. To check if the bucket is created, use the command:

![2ss](https://github.com/harshartz/AWS-EC2/assets/130890384/cbedb5a7-bb47-44b6-8daa-443bd250e5f4)


Following command will list all the available buckets, and you should see your newly created bucket

***aws s3 ls***

![3ss](https://github.com/harshartz/AWS-EC2/assets/130890384/9fcd5ea4-532e-4ea8-859b-da9cdbe25b7b)


# Step 2: Upload Website Files

To upload files to your bucket, use the command:

***aws s3 sync PATH_OF_LOCAL_DIRECTORY s3://BUCKET-NAME***

Replace (PATH OF LOCAL DIRECTORY) with the path of your local directory containing the website files, and (BUCKET-NAME) with the name of your bucket. To check the uploaded files, use the command:

![4ss](https://github.com/harshartz/AWS-EC2/assets/130890384/012e7d45-3ff7-46cf-8cdb-d3d0182d7e89)

![5ss](https://github.com/harshartz/AWS-EC2/assets/130890384/af7f7b4c-f7e7-40cc-91dc-075d29ef0d2f)


Following command will list all the files in your bucket.

***aws s3 ls s3://BUCKET-NAME***

![6ss](https://github.com/harshartz/AWS-EC2/assets/130890384/38b430d1-8fcc-45c9-bf32-8ecd57ddaf00)


# Step 3: Static Website Hosting

To enable static website hosting for your bucket, use the command:

***aws s3 website s3://BUCKET-NAME/ --index-document INDEX-DOCUMENT-NAME --error-document error.html***

Replace (BUCKET-NAME) with your bucket name and (INDEX-DOCUMENT-NAME) with the name of your index document. This command configures the bucket to serve the specified index document and error page.

![7ss](https://github.com/harshartz/AWS-EC2/assets/130890384/b5441b92-9eac-4f23-8bf1-d28584025d01)


# Step 4: Enable Public Access

To make the bucket publicly accessible, use the command:

***aws s3api put-public-access-block --bucket BUCKET-NAME --public-access-block-configuration "BlockPublicAcls=false,IgnorePublicAcls=false,BlockPublicPolicy=false,RestrictPublicBuckets=false"***

Replace (BUCKET-NAME) with your bucket name. This command disables the restrictions on public access to the bucket.

![8ss](https://github.com/harshartz/AWS-EC2/assets/130890384/4542a7d5-111c-485f-a80c-7a673845f433)


# Step 5: Attach Bucket Policy

Create a file using a text editor, such as Notepad, and write your bucket policy in JSON format. Here's an example policy:
Replace (BUCKET-NAME) with your bucket name in the policy. Save the file.

![9ss](https://github.com/harshartz/AWS-EC2/assets/130890384/0d4c304c-60e6-437e-9323-af665af90175)


Save the file with a .json extension.

![10ss](https://github.com/harshartz/AWS-EC2/assets/130890384/1f0329bf-01d2-4d48-be5b-2e08d77ab608)


Use the following command to upload and attach the policy to your bucket:

***aws s3api put-bucket-policy --bucket BUCKET-NAME --policy file://FILE-PATH***

Replace (BUCKET-NAME) with your bucket name and (FILE-PATH) with the path to the policy file you created.

![11ss](https://github.com/harshartz/AWS-EC2/assets/130890384/dcd8bc54-85db-43d2-97b9-b45ae3732041)


# That's it! Your website is now up and running.

The endpoint format for a static website hosted in an S3 bucket is: 

***http://BUCKET-NAME.s3-website-AWS-REGION.amazonaws.com***

Replace (BUCKET-NAME) with your bucket name and (AWS REGION) with your default region (the one you set during configuration). Opening this endpoint will allow you to check if the website is running correctly.

![12ss](https://github.com/harshartz/AWS-EC2/assets/130890384/4f53758e-0a96-4748-9f11-1f4c1420a78b)

![13ss](https://github.com/harshartz/AWS-EC2/assets/130890384/699a8828-22a3-483b-8631-93862770bfde)
