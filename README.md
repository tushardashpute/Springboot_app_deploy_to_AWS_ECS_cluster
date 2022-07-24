# Springboot_app_deploy_to_AWS_ECS_cluster
Deploy a Spring Boot App on AWS ECS Cluster


Introduction

Amazon Elastic Container Service is a managed container orchestration service which allows you to deploy and scale containerized applications. An overview of the features and pricing can be found at the [AWS website.](https://aws.amazon.com/ecs)

**ECS consists out of a few components:**

- Elastic Container Repository (ECR): A Docker repository to store your Docker images (similar as DockerHub but now provisioned by AWS).
- Task Definition: A versioned template of a task which you would like to run. Here you will specify the Docker image to be used, memory, CPU, etc. for your container.
- ECS Cluster: The Cluster definition itself where you will specify how many instances you would like to have and how it should scale.
- Service: Based on a Task Definition, you will deploy the container by means of a Service into your Cluster.
