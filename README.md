# Springboot_app_deploy_to_AWS_ECS_cluster
Deploy a Spring Boot App on AWS ECS Cluster


Introduction

Amazon Elastic Container Service is a managed container orchestration service which allows you to deploy and scale containerized applications. An overview of the features and pricing can be found at the [AWS website.](https://aws.amazon.com/ecs)

**ECS consists out of a few components:**

- Elastic Container Repository (ECR): A Docker repository to store your Docker images (similar as DockerHub but now provisioned by AWS).
- Task Definition: A versioned template of a task which you would like to run. Here you will specify the Docker image to be used, memory, CPU, etc. for your container.
- ECS Cluster: The Cluster definition itself where you will specify how many instances you would like to have and how it should scale.
- Service: Based on a Task Definition, you will deploy the container by means of a Service into your Cluster.

1. Create the App

https://github.com/tushardashpute/springboohello-CICD.git

Run the build in order to create the jar file 

mvn clean install

2. Upload Image to ECR

Navigate in AWS to the ECS Service and select in the left menu the Repositories section. First thing to do, is to create a repository by clicking the Create repository button. In order to see how you can push the Docker image to the repository, click the View push commands button which is available in the repository overview.

aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin ***********.dkr.ecr.us-east-2.amazonaws.com

docker build -t springdemo .

docker tag springdemo:latest ***********..dkr.ecr.us-east-2.amazonaws.com/springdemo:latest

docker push ***********..dkr.ecr.us-east-2.amazonaws.com/springdemo:latest

After successful upload, the Docker image is added to the repository.

<img width="1237" alt="image" src="https://user-images.githubusercontent.com/74225291/180633098-88456c6b-42af-4120-9d0d-21687c2482d4.png">


3. Create Task Definition

Now that the Docker image is available in ECR, next thing to do is to create a Task Definition by creating the Create new Task Definition button in the Task Definitions section (left menu).

<img width="1481" alt="image" src="https://user-images.githubusercontent.com/74225291/180633161-efaf379c-33fe-4a85-9d5b-5e7f483c7297.png">

In step 1, choose for an EC2 self managed task and click the Next step button.

750285159662.dkr.ecr.us-east-2.amazonaws.com/springdemo:latest

<img width="1286" alt="image" src="https://user-images.githubusercontent.com/74225291/180640675-c70b2b38-fe73-4ace-84f3-b7d312ec21e9.png">

<img width="1286" alt="image" src="https://user-images.githubusercontent.com/74225291/180640692-f38c51d7-f636-4365-acb9-b6e5f27185f1.png">

<img width="1286" alt="image" src="https://user-images.githubusercontent.com/74225291/180640744-6c5057bc-37cb-4358-b0ff-0bedb36620a8.png">

Click Next

Now Review and Create the task defination.

<img width="1286" alt="image" src="https://user-images.githubusercontent.com/74225291/180640627-84a9a0f3-0060-45eb-8060-de14f8d1af67.png">


<img width="983" alt="image" src="https://user-images.githubusercontent.com/74225291/180640567-54883c3c-bb31-4a66-870d-7a22f700893f.png">


