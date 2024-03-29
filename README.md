# React App For Google Cloud Run

This repository gives you a sample code and instruction to deploy your react application to the google cloud run. 

Prerequisite

* Must have the docker desktop app in your machine. 
* Must have the node version installed in your machine. 

## What is Docker?
Docker is a container platform that allows you to build, test and deploy applications quickly.
A developer defines all the applications and its dependencies in a Dockerfile which is then used to build Docker images that defines a Docker container. Doing this ensures that your application will run in any environment.

## What is a Container?
A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another. 

Note: You can clone this project and follow the below commands

```
To Build The Application
	docker build -t app .
To Run Docker App
	docker run -p 8080:8080 app 
To Run It In M1 or M2 apple chip	
    docker buildx build  --platform linux/amd64  -t app . 

```

Once you succesfully build the docker app, you can open your docker desktop and check whether your app is running or not. 

## Steps to deploy the project to your google cloud run

Before doing the below steps, make sure that you have gcloud installed in your machine and the default project is selected using the gcloud command before you are deploying. 

```
gcloud services enable artifactregistry.googleapis.com

gcloud artifacts repositories create {repo-name} --repository-format=docker --location=us-central1 --description="created repo"

gcloud auth configure-docker us-central1-docker.pkg.dev

docker tag {local-image-name} us-central1-docker.pkg.dev/{project-name}/{repo-name}/{gcp-image-name}

docker push us-central1-docker.pkg.dev/{project-name}/{repo-name}/{gcp-image-name}
```



