## Lab Four: Starting with AWS CodeStar
If your following through the AWS DevOps Bootcamp presentations, by now you have probably 
talked about AWS CodeStar. You are also probably asking yourself WHY DIDN'T WE START HERE!!?? 
CodeStar allows you to spin up DevOps CICD pipelines for many common workloads. It is a great 
starting point for almost any AWS workload. Let's jump in.

### Step 1: Launching a Project
- On the AWS Dashboard go to **CodeStar**
- Click **Start a project**
- If you get a **Create service role** modal, click **Yes, create role**

### Step 2: Select a Template
- Filter your choices by choosing **Web Application** for the **Application Category** on the left menu
- Filter your choices further by choosing **Node.js** for your **Programming Language** on the laft menu
- Choose **Node.js**, **Amazon EC2** by clicking on the menu item.

### Step 3: Project Details
- In the **ProjectName** box type **BootCamp**
- Select **AWS CodeCommit**
- For the **Repository name** enter **BootCampRepo**
- Click **Next**

### Step 4: Review Project Details
- Ensure that the **AWS CodeStar would like permission to administer AWS resources on your behalf** checkbox is checked
- Click **Create Project**
- In the **Choose an Amazon EC2 Key Pair** modal, choose the Key Pair you created earlier today.
- Check the **Acknowledgement that you have the file** checkbox
- Click **Create Project**

### Step 5: First time here info
- In the **Display Name** field enter your name
- In the **Email** field enter your email
- Click **Next**

### Step 6: Set Up Tools
- Click the **AWS Cloud9** option
- Click **Next**

### Step 7: Set up you AWS Cloud9 environment
Leave all defaults and click **Next**

### Step 8 Explore while you wait
While you wait for everything to get setup, take a look around. You'll see links down the left hand side that 
will take you everywhere you need to go.

### Step 9 Check out your website
When the dashboard is finished loading you will see an **Application Endpoints** section, click on the link to see the resulting website.

That's It!! You have just complete setting up an entire development CICD pipeline and infrastructure.

| [Home](../../README.md) |