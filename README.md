# CI/CD Pipeline Implementation for ABC Technologies (Retail Company)

## Problem Statement

ABC Technologies is a retail organization that requires a faster and more agile approach to application development, testing, and deployment.  
The existing manual process is time-consuming and inefficient, leading to slower releases and reduced reliability.

The goal of this project is to implement an **end-to-end CI/CD pipeline** that automates the build, test, and deployment process using DevOps tools.

---

## Solution Overview

To solve this problem, a **CI/CD pipeline** is designed and implemented using industry-standard DevOps tools.  
The pipeline enables:

- Continuous Integration (CI)
- Continuous Delivery/Deployment (CD)
- Automated build and testing
- Containerized deployment
- Scalable and highly available application delivery

---

## Project Description

- **Project Name:** CI/CD Pipeline for ABC Technologies  
- **Application Type:** Java-based Retail Application  
- **Source Code:** Sample Java project from Edureka DevOps PGP LMS (Project 1)  
- **Build Tool:** Maven  
- **CI Tool:** Jenkins  
- **Containerization:** Docker  
- **Orchestration:** Kubernetes  
- **Configuration Management:** Ansible  

### Source Code Structure
- `src/main` → Application source code  
- `src/test` → Unit test cases  

> **Note:** Jenkinsfile and Dockerfile are created manually as part of this project.

---

## Project Objective

The main objective of this project is to demonstrate the real-world use case and integration of DevOps tools such as:

- Git & GitHub
- Jenkins
- Maven
- Docker
- Ansible
- Kubernetes

This pipeline improves development speed, reliability, and scalability.

---

## Pre-requisites

- Java codebase downloaded from Edureka LMS (Project 1)
- GitHub account
- Jenkins installed on virtual machine
- Docker, and Kubernetes setup
- Docker Hub account for image storage

---

## Tools and Technologies Used

### 1. Source Code Management
- **Git** – Version control system  
- **GitHub** – Cloud-based repository  

### 2. Continuous Integration
- **Jenkins** – Automates build and test process  

### 3. Build Tool
- **Maven** – Compiles, tests, and packages the application  

### 4. Deployment Tool
- **Docker** – Containerizes the application  

### 5. Container Orchestration
- **Kubernetes** – Manages containers in a highly available environment  

---

## Implementation Steps

### Step 1: Source Code Management (Git)

The source code was initially downloaded from the LMS and stored on the local machine.

**Tool Used:** Git Bash

#### Initialize Git Repository
To start tracking the project directory:

```bash
git init
```


#### Check Repository Status
To view untracked files:

```bash
git status
```

#### Add Files to Staging Area
To move untracked files to staging:

```bash
git add .
```
#### Verify Tracked Files
```bash
git status
```

#### Commit the Codebase
To save the code into the local repository:

```bash
git commit -m "Initial commit of codebase"
```
#### Verify Commit
To view commit ID, branch, and commit message:

```bash
git log --oneline
```


#### Confirm Clean Working Tree

```bash
git status
```


---

###  Step 2: Push Code to GitHub (Remote Repository)

Since Jenkins could be installed on a separate virtual machine, the source code must be stored in a remote repository.

**Tool Used:** Github

Logged in to GitHub account and created a new repository named:

amizak_igp_2025

#### Verify Git exist remotely
Before adding a remote, check if any remote repository already exists:

```bash
git remote -v
```

#### Since no remote existed we  proceed to add one
```bash
git remote add origin "url"
```

#### Verify that the remote has been added successfully
```bash
git remote -v
```
#### Push codebase to github
Upload the entire local codebase to Github repository

```bash
git push -u origin master
```
#### Then refresh your Github repository homepage, the complete source code should now be visible.


### Step 3: Integration and Build(Continous integration)

In this phase, Jenkins is used to fetch the code from GitHub, build it, run tests, and package the application.

**Tool Used:** Jenkins and Maven

### Build Part 1: Jenkins & Maven Setup (Pre-requisites)
#### Environment Setup

- **Virtualization Tool:** VirtualBox

- **Operating System:** Ubuntu Linux

**Installed Tools:** Jenkins, Maven, Git, Java (JDK)

### Pre-requisite Checks
#### 1. Verify Jenkins Installation
Ensure Jenkins is installed and properly configured.

#### 2. Verify Java Installation.
Jenkins requires Java to run.

```bash
Java -version
```

#### 3. Restart and enable Jenkins

```bash
sudo systemctl restart Jenkins
sudo systemctl enable Jenkins
systemctl status Jenkins
```
#### 4. Access Jenkins browser
Open a browser and navigate to:

```bash
http://(public_IP_VM):8080
```
> Ensure Port 8080 is allowed in firewall or security group

### Build Part 2: Maven & Git Verification
This stage ensures the Jenkins server can build and manage the codebase. By running commands like mvn compile, mvn test and mvn package.

#### 1. Verify Maven Installation on the same VM/Server Jenkins is installed.
```bash
mvn -version
```
If not install Maven
> Confirm Maven home directory exists (e.g., /opt/maven).

#### 2. Verify Git Installation on the same VM/Server Jenkins is installed
```bash
git -version
```
> Git is required so Jenkins can clone the GitHub repository during the pipeline execution.
> Ensure Maven and Git are installed on the same Vm were Jenkins is installed.


### Step 4: Continuous Integration Pipeline
This Continuous Integration pipeline is implemented using Jenkins Pipeline and is responsible for fetching the source code using Git, compiling it, running unit tests, and generating the deployment artifact using maven. All these steps will be done or achieved on the integration tool (Jenkins).

#### Integration Objective:
Jenkins performs the following actions:
1. *Checkout:*Pulls code from GitHub
2. Compiles the application.
3. *Test:* Runs unit tests
4. Packages the application using Maven
5. Archives build artifacts.




### Create Jenkins Continous Integration Pipeline Job

1. Log in to Jenkins Dashboard
2. Click New Item
3. Type of the Job, Select Pipeline
4. Enter a job name (CI-Job)
5. Write script  to perform the CI in the pipeline
6. Define pipeline stages in a Jenkinsfile
7. The pipeline script handles checkout, build, test, and package stages, all executed automatically after running the script.


#### Pipeline Execution Environment
The pipeline is configured to run on any available Jenkins node. This means it can execute on either Jenkins master, or any configured agent (slave) node.

### Stage 1: Checkout (Source Code Retrieval)
In this stage, Jenkins downloads the complete source code from the GitHub repository.

#### Source Control Tool: Git
Action Performed: Clone the entire codebase
Repository URL: GitHub repository URL
This ensures Jenkins always works with the latest version of the code.

### Stage 2: Compile (Build Stage)
Once the code is checked out, it must be compiled so the system can understand and execute it.

#### Programming Language: Java (High-Level Language)
#### Build Tool: Maven
Command Used:
```bash
sh 'mvn compile'
```
Compilation converts high-level Java code into machine-readable bytecode. This stage verifies that the code has no syntax or compilation errors
> The sh keyword in Jenkins is used to execute shell commands on the Jenkins server.

### Stage 3: Test (Unit Testing)
In this stage, unit test cases written by the development team are executed.

#### Test Type: Unit Tests
Tool Used: Maven

#### Responsibility:
1. Tests are written by developers
2. Execution is handled by the DevOps CI pipeline

#### Purpose:
Ensures application stability
Detects issues early before deployment

### Stage 4: Package (Build Artifact Creation)
After successful compilation and testing, the final deployment artifact is generated.
#### Artifact Type: .war file (Web Archive)

#### Final Output File:
```bash
abctechnologies.war
```
> The pom.xml file defines the packaging type as WAR
> This WAR file is the final deployment artifact

#### Build Output Location
After the pipeline execution, the artifact is stored on the Jenkins server at:
```bash
/var/lib/jenkins/workspace/ci-job/target/abctechnologies.war
```
> This artifact will be used in the deployment stage, where it is containerized using Docker.

#### Jenkins Job Execution Details
Installation User: root
(All tools such as Jenkins, Maven, and Git were installed by the root user)

#### Execution User: jenkins
(All Jenkins jobs run under the jenkins user)

#### Job Workspace Location:
/var/lib/jenkins/workspace/ci-job


### Continuous Deployment (CD) Using Docker
Overview
This stage extends the Continuous Integration pipeline into a full CI/CD pipeline by adding deployment automation using Docker.
The deployment is executed on the same virtual machine where Jenkins is installed.

#### Tools & Technologies
Jenkins
Docker
Git & GitHub
Maven
Apache Tomcat
Docker Hub

#### Environment Setup
Install Docker
Docker is installed on the same virtual machine where Jenkins is running to enable Docker-based deployment.
Jenkins User Permissions
Jenkins jobs are executed by the jenkins user.
To allow Docker commands to run during pipeline execution, permissions are granted on the Docker socket:
```bash
sudo chown root:jenkins /var/run/docker.sock
```
#### Dockerfile Configuration
The application is containerized using a Dockerfile.

#### Artifact Type: WAR file
Artifact Name: ABCtechnologies-1.0.war
Packaging type is defined in pom.xml
Apache Tomcat is used to run the application

#### The WAR file is copied to the Tomcat deployment directory:
```bash
/usr/local/tomcat/webapps/
```

#### Tomcat is started using catalina.sh run, which automatically deploys the WAR file.
Version Control for Dockerfile

#### The Dockerfile is:
Stored alongside the source code, Tracked using Git, Committed and pushed to GitHub.
This allows Jenkins to retrieve the Dockerfile during the checkout stage and track configuration changes.

CI/CD Pipeline Workflow (ci-cd-job)
#### Stage 1: Checkout
Jenkins clones the GitHub repository, including:
1. Source code
2. pom.xml
3. Dockerfile

#### Stage 2: Build and Test
Maven is used to compile, test, and package the application:
Artifact output location:
/var/lib/jenkins/workspace/$JOB_NAME/target/ABCtechnologies-1.0.war

#### Stage 3: Prepare Artifact for Docker Build
For Docker image creation, the WAR file and Dockerfile must be in the same directory.

The artifact is copied to:
/var/lib/jenkins/workspace/$JOB_NAME/ABCtechnologies-1.0.war

#### Stage 4: Docker Image Build
The Docker image is built using:
```bash
docker build -t ABCtechnologies:$BUILD_NAME .
```
$BUILD_NAME is used for dynamic versioning
Prevents hardcoding build numbers

#### Stage 5: Docker Image Tagging
The image is tagged before pushing to Docker Hub
Docker Hub Authentication
Docker Hub credentials are stored securely in Jenkins Global Credentials.
Credential ID: mydockerhubcred
Docker Pipeline plugin is installed on Jenkins
Jenkins is restarted before pipeline execution
> Note: Credentials are never stored in plain text

#### Stage 6: Push Image to Docker Hub
docker push amizak/ABCtechnologies:$BUILD_NUMBER

#### Stage 7: Deploy Application Container
The application is deployed as a Docker container:
docker run -d -p <host_port>:8080 amizak/ABCtechnologies:$BUILD_NUMBER


#### Check running containers:
docker ps -a
Application Access
The deployed application can be accessed via a web browser:
```bash
http://<Public_IP_VM>:<host_port>/ABCtechnologies-1.0
```



### Kubernetes Deployment – IGP Application
#### Overview
This repository contains the Kubernetes deployment configuration for the IGP project ABCtechnogies application.
The application is deployed on a MicroK8s Kubernetes cluster using a locally hosted container registry. The deployment runs a containerized Java application ABCtechnogies.war and exposes it internally within the cluster.

#### Kubernetes Deployment Details
1. Cluster Type: MicroK8s
2. Workload Type: Deployment
3. Replicas: 1
4. Container Runtime: Docker
5. Image Registry: MicroK8s local registry (localhost:32000)
6. Container Port: 8080

#### Deployment manifest
Create a deployment.yaml file and push it to github after tracking and committing it.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: igp-app
spec:
  replicas: 1
  selector:
    matchLabels:
      app: igp-app
  template:
    metadata:
      labels:
        app: igp-app
    spec:
      containers:
        - name: igp-container
          image: localhost:32000/igp_2025:IMAGE_TAG
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 8080

```
> IMAGE_TAG is dynamically replaced during deployment to reference the correct container image version.
> imagePullPolicy is set to IfNotPresent to ensure the image is pulled from the local registry.
> The container listens on port 8080.

#### Deployment steps:
1. Update Image Tag
Replace the placeholder image tag with the actual image reference.
```bash
sed -i "s|IMAGE_TAG|localhost:32000/igp_2025:1|g" deployment.yaml
```

#### Apply the Deployment
Deploy the application to the Kubernetes cluster.
```bash
microk8s kubectl apply -f deployment.yaml
```

Check the deployment status:
```bash
microk8s kubectl get deployments
```

Check running pods:
```bash
microk8s kubectl get deployments
```
Check running pods:
```bash
microk8s kubectl get pods
```

Describe a pod for more details:
```bash
microk8s kubectl describe pod <pod-name>
```

#### Kubernetes Dashboard
The Kubernetes Dashboard can be used to visually confirm the deployment.
1. Enable and access the dashboard:
```bash
microk8s enable dashboard
```

```bash
microk8s dashboard-proxy
```

2. Access in a browser:
   ```cpp
   https://127.0.0.1:10443
   ```
   
#### Container Registry
The deployment pulls images from the MicroK8s local container registry:
  ```txt 
   localhost:32000/igp_2025:<tag>
  ```

Ensure the registry is enabled:
```bash
microk8s enable registry
```

### Author
#### Alek(YUSUF ALEAKHUE UMAR)



