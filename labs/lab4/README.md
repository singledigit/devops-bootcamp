## Lab Four: Starting with AWS CodeStar
If your following through the AWS DevOps Bootcamp presentations, by now you have probably 
talked about AWS CodeStar. You are also probably asking yourself WHY DIDN'T WE START HERE!!?? 
CodeStar allows you to spin up DevOps CICD pipelines for many common workloads. It is a great 
starting point for almost any AWS workload. Let's jump in.

## Some Housekeeping
Before we start spinning up more resources, lets do some cleanup to make sure we are not 
paying for something we are not using.

***Before we start: Please note that any data stored on these machines will be lost***
If you stored something you want to keep, grab it now.

## Step 1: Delete our Pipeline
- On the AWS Dashboard go to the **CloudFormation** dashboard.
- Check the box next to **Pipeline**
- On the Resources tab find the only S3Bucket and make note of the name (we will use this shortly)
- On the **Actions** dropdown, choose **Delete Stack**
- On the **Delete Stack** modal click **Yes Delete**

## Step 2: Delete the Pipeline Bucket
- On the AWS Dashboard go to the **S3** dashboard
- Click on the **Bucket Icon** next to the name of your Pipeline bucket.
- Click the **Delete bucket** button
- On the **Delete bucket** modal, type the name of the bucket (Hint: Copy and Paste)
- Click **Confirm**

"Why wasn't this deleted with the rest of the stack?". CloudFormation does not delete an S3 bucket 
with data in it. We need to manually delete.

## Step 3: Delete the Infrastructure
Use the following command in the terminal to delete the **Infrastructure** Stack
```
aws cloudformation delete-stack --stack-name Infrastructure
```