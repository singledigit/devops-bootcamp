## Lab Three: Deploying the Code
In lab one we launched an infrastructure to host our code and in lab two we built a pipeline 
to automatically merge and build our code (Continuous Integration). Now we want to connect the dots
by automatically deploying our prepared code to our infrastructure (Continuous Delivery).

## Updating our Infrastructure
In order for our deployment stack to be able to identify it's deployment targets, 
we are going to give the instances an identifying tag.

### Step 1: Exploring the differences
Take a look at the "lab1.yaml" file in your **do-bc** and compare it to the "lab3-arch.yaml" file. 
You will notice that the files are identical except for some commented out parts in lab1. 
We are adding the **Tags** section to the instance.

### Step 2: Create a Change-Set
- Make sure you are in the **do-bc** directory
```
cd ~/environment/do-bc
```
- Run the following command create a change-set with these changes
```
aws cloudformation create-change-set --stack-name Infrastructure --change-set-name Infra2 --template-body file://./lab3-infra.yaml --parameters ParameterKey=KeyPairName,UsePreviousValue=true ParameterKey=VpcId,UsePreviousValue=true ParameterKey=ProjectId,ParameterValue=bootcampapp --capabilities CAPABILITY_NAMED_IAM
```
- Validate change-set
```
aws cloudformation describe-change-set --stack-name Infrastructure --change-set-name Infra2
```
This will report the status of the change-set. You should see that the **ExecutionStatus** is available.

### Step 3: Execute the Change-Set
Run the following command to execute
```
aws cloudformation execute-change-set --stack-name Infrastructure --change-set-name Infra2
```

### Step 4: Check for Completion
Run the following command in your terminal to check the status of your stack.
```
aws cloudformation describe-stacks --stack-name Infrastructure
```
You will eventually see a **StackStatus** of **UPDATE_COMPLETE**.

When you do, then your EC2 Instance has now been tagged with the tag **bootcampapp-WebApp**

If you still have a link to your "Hello World" website up, refresh it to see that it is still up and running.

## Updating Our Pipeline
Now that we have identifiable targets for our deployment. Let's update our Pipeline to add a deployment stage.

### Step 1: Create a Change-Set
- Make sure you are in the **do-bc** directory
```
cd ~/environment/do-bc
```
Run the following command to create a change set on the **Pipeline** stack.
```
aws cloudformation create-change-set --stack-name Pipeline --change-set-name Pipe2 --template-body file://./lab3-pipe.yaml --parameters ParameterKey=KeyPairName,UsePreviousValue=true ParameterKey=VpcId,UsePreviousValue=true --capabilities CAPABILITY_NAMED_IAM
```
- Validate Change-Set
```
aws cloudformation describe-change-set --stack-name Pipeline --change-set-name Pipe2
```
This will report the status of the change-set. You should see that the **ExecutionStatus** is available.

### Step 2: Execute the Change-Set
- Run the following command to execute
```
aws cloudformation execute-change-set --stack-name Pipeline --change-set-name Pipe2
```

### Step 3: Check for Completion
Run the following command in your terminal to check the status of your stack.
```
aws cloudformation describe-stacks --stack-name Pipeline
```
If you run that coomand several times, you will eventually see a **StackStatus** of **UPDATE_COMPLETE**.

### Step 4: Check the results
- On the AWS Dashboard choose the CodePipeline service. This will take you to the CodePipeline console which gives you access to the Source, Build, Deploy, and Pipeline resources.
- Click on the **bootcampapp-Pipeline** in the Pipelines list.
- Take a look at the bootcampapp-Pipeline. You should now have three stages: Source, Build, Deploy
- However, as of yet, a release has not been deployed

## Creating a Release

Now that we have a full working pipeline, it's time to create a release. However, as we learned in the presentation, 
if we are going to use CodeDeploy, we need an appspec file. No worries, I have you covered.

### Step 1: Pushing the required files
- Run the following command in the terminal to copy the **appspec** file and supporting files in to our **BootCampRepo**
```
cp -R ~/environment/do-bc/site2/* ~/environment/BootCampRepo/.
```
- Add the changes to the local and then the CodeCommit repoository by running the following commands.
```
cd ~/environment/BootCampRepo
```
```
git add -A && git commit -am "Adding appspec resources"
```
```
git push
```

### Step 2: Check the results
- On the AWS Dashboard choose the CodePipeline service. This will take you to the CodePipeline console which gives you access to the Source, Build, Deploy, and Pipeline resources.
- Click on the **bootcampapp-Pipeline** in the Pipelines list.
- Take a look at the bootcampapp-Pipeline. You will see that your full pieline is now running or it will have already run.

### Step 3: Check your website
- If you still have a link to your website, refresh it! Does it look better?
- If you do not, on the **AWS Dashboard** got to **CloudFormation** and check the box next to the **Infrastructure** stack. Look under the outputs tab below.

Hopefully you see an updated site, if you don't see one... don't worry, we will 
talk about this in a later session but for now you can try forcing a new release.

### Optional Step 4: Create a new release
Releases can be created several ways.

1. Committing new code like we just did. Try changing some of the text in the **index.html** file under the **BootCampRepo** file and run the `git` parts of **Step 1** again.
2. Clicking on the **Release change** button on the **CodePipeline** dashboard.
3. Through the CLI using the following code.
```
aws codepipeline start-pipeline-execution --name bootcampapp-Pipeline
```

| [Home](../../README.md) |