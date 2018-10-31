## Lab Three: Deploying the Code
In lab one we launched an infrastructure to host our code and in lab two we built a pipeline 
to automatically merge and build our code (Continuous Integration). Now we want to connect the dots
by automatically deploying our prepared code to our infrastructure (Continuous Delivery).

## Updating our Infrastructure
In order for our deployment stack to identify we are going to use the Tagging method. We will
give the instances an identifying tag.

### Step 1: Exploring the differences
- Take a look at the "lab1.yaml" file in your *do-bc* and compare it to the "lab3-arch.yaml" file.
- You will notice that the files are identical except for some commented out parts in lab1.
- We are adding the **ProjectId** parameter and the **Tags** section to the instance.

### Step 2: Create a Change-Set
- Make sure you are in the *do-bc* directory
```
cd ~/environment/do-bc
```
- Run the following command create a changeset with these changes
```
aws cloudformation create-change-set --stack-name Infrastructure --change-set-name Infra2 --template-body file://./lab3-arch.yaml --parameters ParameterKey=KeyPairName,UsePreviousValue=true ParameterKey=VpcId,UsePreviousValue=true ParameterKey=ProjectId,ParameterValue=bootcampapp
```
- Validate Change-Set
```
aws cloudformation describe-change-set --stack-name Infrastructure --change-set-name Infra2
```
This will report the status of the change-set. You should see that the *ExecutionStatus* is available.

### Step 3: Execute the Change-Set
- Make sure you are in the *do-bc* directory
```
cd ~/environment/do-bc
```
- Run the following command to execute
```
aws cloudformation execute-change-set --stack-name Infrastructure --change-set-name Infra2
```

### Step 4: Check for Completion
Run the following command in your terminal to check the status of your stack.
```
aws cloudformation describe-stacks --stack-name Infrastructure
```
You will eventually see a *StackStatus* of *UPDATE_COMPLETE*.

When you do, then your EC2 Instance has now been tagged with the tag *bootcampapp-WebApp*

## Updating Our Pipeline
Now that we have identifiable targets for our deployment. Let's update our Pipeline to add a deployment stage.

### Step 1: Create a Change-Set
- Make sure you are in the *do-bc* directory
```
cd ~/environment/do-bc
```
Run the following command to create a change set on the *Pipeline* stack.
```
aws cloudformation create-change-set --stack-name Pipeline --change-set-name Pipe2 --template-body file://./lab3-pipe.yaml --parameters ParameterKey=KeyPairName,UsePreviousValue=true ParameterKey=VpcId,UsePreviousValue=true --capabilities CAPABILITY_NAMED_IAM
```
- Validate Change-Set
```
aws cloudformation describe-change-set --stack-name Pipeline --change-set-name Pipe2
```
This will report the status of the change-set. You should see that the *ExecutionStatus* is available.

### Step 2: Execute the Change-Set
- Make sure you are in the *do-bc* directory
```
cd ~/environment/do-bc
```
- Run the following command to execute
```
aws cloudformation execute-change-set --stack-name Pipeline --change-set-name Pipe2
```