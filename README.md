# simple-docker-App
Deploy a simple docker app using AWS ECS and ECR
## Create an ECR repository and push the image built from the Dockerfile into it
Go to the ECR AWS console and create a public repository. Give it a name, scroll down and click on "Create Repository"

![image](https://user-images.githubusercontent.com/108973856/232793205-a089e639-99ca-4da4-ae4c-9562b0335d80.png)

Now select the repository and click on view push commands.

![image](https://user-images.githubusercontent.com/108973856/232796159-fdc1c90f-7f40-4df4-99f7-af2942127c05.png)

Follow the instructions on screen one by one to complete building the image and upload it to ECR repository.

## Set up ECS Cluster and Task Definition
- Go on to the ECS AWS console, click on create cluster, and give it a name. On Infrastructure selection, keep "AWS Fargate (serverless)" selected and leave everything else to default. Click on create and your ECS cluster will be ready in few seconds.
- Click on `Task Definitions` from the left menu and then click on `Create new task definition`.
- Give it a name.
- On the container section, give the container a name.
- Copy the URI from the ECR repository and fill in the `Image URI` field with that.
- Take the port from the Dockerfile and fill the `Container port` field with that.
- Leave rest of the things to default and click on `Next`.
- Reduce the CPU to .5vCPU and Memory to 2GB.
- With the remaining set to default click on `Next`.
- Now review and click on `Create`. 

## Deploy the conatiner
- Now come into the cluster created earlier.
- Click on `Tasks` followed by `Run new task`.
- For Compute configuration select "Launch type".
- Under Deployment configuration select `Task` as the Application type.
- On the Family dropdown select the Task Definition createed in previous steps.
- For the Desired tasks, keep 1 for now.
- Under Networking, let the VPC and subnet be default.
- Create a security group and allow access to port 3000 from anywhere.
- With the remaining left to default click on `Create`.

## Accessing the App
- Now open the task created.
- Click on `Network bindings`.
- Copy the `External link` and open in a browser window.

![image](https://user-images.githubusercontent.com/108973856/232814603-2dd17d5b-95d1-4b1a-8764-8364f02f5c27.png)

## The App
![image](https://user-images.githubusercontent.com/108973856/232815155-4294d808-ea43-4d39-a1b7-f43b6e080d6b.png)



