## Purpose

### Upload your local docker image to Elastic Container Registry (ECR)

Navigate to this link first to configure your AWS CLI with the proper credentials:

https://confluence/display/~JBilliau/AWS+Class

Once done, copy and paste the following commands in your terminal window:

1. aws ecr get-login --no-include-email --region us-east-2 --no-verify-ssl

If the above command fails with an invalid security token, open your credentials file in a text editor (probably C:\Users\yourname\.aws\credentials) and delete the line starting with aws_session_token, then run the command again.

2. Take outputted "docker login" command, copy and paste it and run it)

3. docker tag **YOURNAME:YOURVERSION** 418023852230.dkr.ecr.us-east-2.amazonaws.com/training-ecr:**YOURNAME**

4. docker push 418023852230.dkr.ecr.us-east-2.amazonaws.com/training-ecr:**YOURNAME**

### Create ECS Task Definition
This is the blueprint for your application, the ECS equivalent of the docker compose file. It controls what image to run, how many resources to grant, environment variables, logging, etc.

1. Login to awsconsole and navigate to the ECS console. Click **Task Definitions**. 
2. Click **Create new Task Definition**. On the next screen, click **FARGATE** and then next step.
3. For *Task Definition Name*, put in your first initial and last name. 
4. For *Task Role*, select "None".
5. For *Task Execution Role*, make sure it's set to "ecsTaskExecutionRole*. For *Task Size*, select **1GB** for Task Memory, **.5 vCPU** for Task CPU.
6. Scroll down and click **Add Container**. 
    * For *Container name*, put in your first initial, last name again.
    * for *Image*, put in the link to your ECR image you uploaded:
    * For *Memory limits*, put in **128**.
    * For *Port mappings*, put in **80** for the "container port".
    * Scroll all the way down and click **Create**. If successful, click **View Task Definition** to go back to the main console area.

### Create ECS Service
Amazon ECS allows you to run and maintain a specified number of instances of a task definition simultaneously in an Amazon ECS cluster. This is called a service. This controls how many containers to run, scaling policies, networking configuration, etc.

1. Click **Clusters**, then **click test-ecscluster-418023852230-us-east-2**.
2. Under the *Services* tab, click **Create**.
    * For *Launch Type*, click **FARGATE**.
    * For *Task Definition*, select your name for the "Family", then *1 (latest)* for the "revision".
    * For *Service name*, put in your first initial, last name.
    * For *Number of Tasks*, put in 1. Scroll all the way down, click **Next Step**.
    * Uncheck *Enable service discovery integration*, then scroll up a bit to the *VPC and security groups* section.
    * For *Cluster VPC*, select **vpc-08850982ee9a0f0a1**. For *Subnets*, select one with the word **PUBLIC** in the name, doesnt matter which. Ensure *Auto-assign public IP* is enabled.
    * Click **Next Step** twice, then **Create Service**.
    * You will be taken to the status screen for your service. Hit refresh on the right hand side until you see a task appear and go to the *last status* of **RUNNING**. This means
    your container is running successfully. Click the **Task** link (long guuid-like number). Under the *Network* section, you will see a **Public IP*. Copy and paste it into your browser
    and you should see your container's web page!