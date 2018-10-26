## Lab Two: Building the Pipeline
Welcome to your second lab of the AWS DevOps Bootcamp!! In the previous lab you 
launched your first stack you launched a media rich website called "hello world".
But If you want to update the code for the website, wou would have to change the 
Cloudformation stack and run it all again... manually.

In this Lab we are going to start building the beginnings of a Continuous Integration/Continuous Deployment
process. Lets get started.

## Launching the Pipeline Stack

### Step 1: Retrieve *KeyPairName* and *VpcId*
- **KeyPairName** is the Key Pair you created in the *Configuration* section. If you do not remember it use the following terminal command to obtain
```
aws ec2 describe-key-pairs
```
- **VpcId** can be obtained with the following terminal command
```
aws ec2 describe-vpcs --query 'Vpcs[?IsDefault==`true`].VpcId' --output text
```

### Step 2: Update and run command
- Copy the following command to your terminal (Yep, it's a long one)
- Update the <placeholders> with the values you retrieved in *Step 1*. Make sure ther "<" and ">" are removed too.
- Hit **Enter** to run
```
aws cloudformation create-stack --stack-name Pipeline --template-body file://./lab2.yaml --parameters ParameterKey=KeyPairName,ParameterValue=<KeyPairName> ParameterKey=VpcId,ParameterValue=<VpcId> --capabilities CAPABILITY_NAMED_IAM
```