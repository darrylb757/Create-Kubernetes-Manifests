# Create-Kubernetes-Manifests
I will set up a deployment manifest that tells Kubernetes how to deploy my backend or my containerized application. 

# Create Kubernetes Manifests


**Author:** Darryl Brown  
**Email:** darrylbrown1991@gmail.com

---

## Create Kubernetes Manifests

![Image](http://learn.nextwork.org/sincere_vermilion_playful_beaver/uploads/aws-compute-eks3_b01876555)

---

## Introducing Today's Project!

In this project, I will set up a deployment manifest that tells Kubernetes how to deploy my backend or my containerized application. I will also set up a Service manifest that tells Kubernetes how to expose my backend to the users. I am doing this because this is a key part in a Kubernetes deployment process.

### Tools and concepts

I used Amazon EKS, eksctl, Git, Amazon ECR, Docker, Kubernetes to create a Kubernetes cluster and build the container image to deploy. Key concepts include using manifests files, deployments and services for Kubernetes deployment.

### Project reflection

I chose to do this project today because show a representation of a creating a Kubernetes manifest and how that ties into the deployment.

This project took me approximately 30-45 minutes. My favorite part was gaining a deeper understand of Kubernetes deployments and how they work within the YAML file. 

---

## Project Set Up

### Kubernetes cluster

To set up today's project, I launched a Kubernetes cluster. Steps I took to do this included granting EC2 permissions over IAM and installing the eksctl command line tool. Created cluster using the eksctl create command.

### Backend code

I retrieved the backend that I plan to deploy by cloning it from my developer team member's Github repository. The backend is the "brain" of an application. It's where the app processes user requests and stores and retrieves data. Unlike frontend code, which is what users see and interact with, backend code works on the server side to make sure the app behaves as expected when a user does things like clicking on buttons.

### Container image

Once I cloned the backend code, I built a container image because the container image lets Kubernetes set up multiple, identical containers so the application runs consistently across different environments. Whether I'm deploying in development, testing, or production, the app behaves the same way because Kubernetes refers to the image each time a new instance/node needs to be created. I used the docker build command, I asked Docker to read the instructions in the Dockerfile and build the container image for me accordingly.

I also pushed the container image to a container registry, because it securely store, share, and deploy container images.
Amazon ECR is an excellent choice for storing a container image because it's an AWS service, which lets Elastic Kubernetes Service (EKS) deploy the container image with minimal authentication setup. To push the image to ECR, I ran the ECR push command in my EC2 instance terminal.

---

## Manifest files

Kubernetes manifests are a set of instructions that tells Kubernetes how to run the app. Kubernetes uses it to know what the app needs, like which containers to run, how many copies to create, and how much memory to allocate. Manifests are helpful because Kubernetes wouldn’t know how to set up and manage the app automatically. This means I'd have to manually configure each container every time I deploy, which would be confusing, error-prone, and hard to repeat. Manifests make deployment simple, clear, and consistent.

A Kubernetes deployment manages multiple copies of the same containerized backend. The container image URL in my Deployment manifest tells Kubernetes the attributes of the container that I'd like Kubernetes to deploy. 

![Image](http://learn.nextwork.org/sincere_vermilion_playful_beaver/uploads/aws-compute-eks3_b01876554)

---

## Service Manifest

A Kubernetes Service exposes the application making it accessible to network traffic instead of application just being accessible from inside the cluster. You need a Service manifest because the deployment manifest takes care of creating and managing the application expect how user or other apps will get access. No service manifest equals no traffic.

My Service manifest sets up a node port and target port, which means it maps traffic that gets port 8080 of the Service to port 8080 of the container running the application. 

![Image](http://learn.nextwork.org/sincere_vermilion_playful_beaver/uploads/aws-compute-eks3_b01876555)

---

## Deployment Manifest

Annotating the YAML files helped me understand the ins and outs of each command in the Deployment manifest because I am breaking down and explaining each line in their relationship to other commands.

A notable line in the Deployment manifest is the number of replicas, which means the number of Pods. Pods are relevant to this because in Kubernetes, Pods are groups of containers that are bundled together so they can work as a unit. Pods are the smallest things you can deploy. You can't deploy containers on their own, they must be inside a Pod. In more technical terms, this means Pods are the smallest deployable units in Kubernetes.

One part of the Deployment manifest I still want to know more about is the name space of a deployment because it's not too clear of how or if it impacts deployment.

![Image](http://learn.nextwork.org/sincere_vermilion_playful_beaver/uploads/aws-compute-eks3_6aae73e71)

---

---
