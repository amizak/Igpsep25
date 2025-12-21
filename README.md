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

<img width="1410" height="492" alt="Image" src="https://github.com/user-attachments/assets/ec18bfbb-f690-4e2d-951f-5e7907e5c9c0" />

**Tool Used:** Git Bash

#### Initialize Git Repository
To start tracking the project directory:

```bash
git init
```

<img width="1893" height="663" alt="Image" src="https://github.com/user-attachments/assets/c21bd76a-10c3-4ff1-b0df-8995e681d1ad" />


#### Check Repository Status
To view untracked files:

```bash
git status
```

<img width="1893" height="663" alt="Image" src="https://github.com/user-attachments/assets/3efb0484-bf32-4e2f-87b4-8469b5e3a7f0" />

#### Add Files to Staging Area
To move untracked files to staging:

```bash
git add .
```
#### Verify Tracked Files
```bash
git status
```

<img width="1893" height="1313" alt="Image" src="https://github.com/user-attachments/assets/63b31e9d-fdfb-4a3e-a7ae-3aee9840bb2c" />

#### Commit the Codebase
To save the code into the local repository:

```bash
git commit -m "Initial commit of codebase"
```

<img width="1893" height="1313" alt="Image" src="https://github.com/user-attachments/assets/f9add925-7891-4342-98e7-b174fddd9665" />

#### Verify Commit
To view commit ID, branch, and commit message:

```bash
git log --oneline
```
<img width="1893" height="1313" alt="Image" src="https://github.com/user-attachments/assets/63b4e6e6-5e4b-4b49-855a-0cc11a24d3f3" />

#### Confirm Clean Working Tree

```bash
git status
```
<img width="1893" height="1313" alt="Image" src="https://github.com/user-attachments/assets/2f16bfbc-74ac-4df0-8710-0afcdadee6db" />

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
<img width="1893" height="1313" alt="Image" src="https://github.com/user-attachments/assets/27d09204-a100-4474-ad47-7cbee6c47cf2" />

#### Since no remote existed we  proceed to add one
```bash
git remote add origin "url"
```
#### Verify that the remote has been added successfully
```bash
git remote -v
```

<img width="1893" height="1313" alt="Image" src="https://github.com/user-attachments/assets/9037242b-1ec1-44cf-a9c7-5d732e5ddb62" />


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

<img width="1905" height="1021" alt="Image" src="https://github.com/user-attachments/assets/7f74a12e-ded2-405d-85ba-27e5319d1d15" />

#### 4. Access Jenkins browser
> Ensure Port 8080 is allowed in firewall or security group

<img width="1905" height="753" alt="Image" src="https://github.com/user-attachments/assets/cddabcf1-40b8-4e58-bb98-b3c71dcf7fee" />

Open a browser and navigate to:

```bash
http://(public_IP_VM):8080
```
<img width="1781" height="1208" alt="Image" src="https://github.com/user-attachments/assets/aa6d2e88-0489-4158-8148-c93cfb0778b6" />

### Build Part 2: Maven & Git Verification
This stage ensures the Jenkins server can build and manage the codebase. By running commands like mvn compile, mvn test and mvn package.

#### 1. Verify Maven Installation on the same VM/Server Jenkins is installed.
```bash
mvn -version
```

<img width="1905" height="283" alt="Image" src="https://github.com/user-attachments/assets/4f7ec0be-c47f-44ec-8ae1-23598460cd32" />

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



----
### Create Jenkins Continous Integration Pipeline Job

1. Log in to Jenkins Dashboard
2. Click New Item
3. Type of the Job, Select Pipeline
4. Enter a job name (CI-Job)
5. Write script  to perform the CI in the pipeline
6. Define pipeline stages in a Jenkinsfile
7. The pipeline script handles checkout, build, test, and package stages, all executed automatically after running the script.

<img width="1758" height="1175" alt="Image" src="https://github.com/user-attachments/assets/ce380198-4fab-4f27-8823-0aecda57bc61" />

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
ci-job script
pipeline
```sh
{
    
    agent any
    stages
    {
    
        stage('Checkout')
        {
            steps
            { 
                git 'https://github.com/amizak/Igpsep25.git'
            }
        }
    
        stage('Compile')
        {
            steps
            {
                sh 'mvn compile'
            }
        }
    
        stage('Test')
        {
            steps
            {
                sh 'mvn package'
            }
        }

        stage('Build')
        {
            steps
            {
                sh'mvn package'
            }
        }
    }
}
```

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

<img width="1574" height="203" alt="Image" src="https://github.com/user-attachments/assets/5f9a935d-8a81-4498-bcda-555c659f5d81" />

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
```txt
FROM iamdevopstrainer/tomcat:base
COPY ABCtechnologies-1.0.war /usr/local/tomcat/webapps/
cmd ["catalina.sh", "run"]
```
-----
CI/CD Pipeline Workflow (ci-cd-job)
#### Stage 1: Checkout
Jenkins clones the GitHub repository, including:
1. Source code
2. pom.xml
3. Dockerfile
<img width="1804" height="159" alt="Image" src="https://github.com/user-attachments/assets/fb539dc6-b719-4e98-bc93-473606899938" />

<img width="1804" height="753" alt="Image" src="https://github.com/user-attachments/assets/958d49f4-457c-4144-87be-36e1b7c4f6eb" />

<img width="1804" height="616" alt="Image" src="https://github.com/user-attachments/assets/c6f96b36-26c5-4e35-acc7-2de0fc7aa380" />

<img width="1760" height="1045" alt="Image" src="https://github.com/user-attachments/assets/dce79fb0-a6a5-4a09-8525-1ecff069b2a4" />

#### Stage 2: Build and Test
Maven is used to compile, test, and package the application:
Artifact output location:
/var/lib/jenkins/workspace/$JOB_NAME/target/ABCtechnologies-1.0.war

<img width="1760" height="1312" alt="Image" src="https://github.com/user-attachments/assets/a7eb8aed-ed04-4c7b-909d-a690279fb9c9" />

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

<img width="1804" height="499" alt="Image" src="https://github.com/user-attachments/assets/638b3521-9712-4e5a-b096-2e5379c5cd13" />

Docker Pipeline plugin is installed on Jenkins

<img width="1804" height="669" alt="Image" src="https://github.com/user-attachments/assets/4184bbe0-170e-4636-b337-ea95b998ce7e" />

Jenkins is restarted before pipeline execution
> Note: Credentials are never stored in plain text

#### Stage 6: Push Image to Docker Hub
docker push amizak/ABCtechnologies:$BUILD_NUMBER

<img width="1195" height="676" alt="Image" src="https://github.com/user-attachments/assets/7b518e1e-5803-4af0-b617-d2be4837a831" />

#### Stage 7: Deploy Application Container
The application is deployed as a Docker container:
docker run -d -p <host_port>:8080 amizak/ABCtechnologies:$BUILD_NUMBER


#### Check running containers:
docker ps -a

<img width="1215" height="676" alt="Image" src="https://github.com/user-attachments/assets/85368e52-abe0-4b85-9cd0-f88d1b546fa9" />

CI-CD-JOB PIPELINE
```sh

pipeline
{
    
    agent any
    stages
    {
    
        stage('Checkout')
        {
            steps
            { 
                git 'https://github.com/amizak/Igpsep25.git'
            }
        }
    
        stage('Compile')
        {
            steps
            {
                sh 'mvn compile'
            }
        }
    
        stage('Test')
        {
            steps
            {
                sh 'mvn package'
            }
        }

        stage('Build')
        {
            steps
            {
                sh'mvn package'
            }
        }

        stage('Build Docker Image')
        {
            steps
            {
                sh 'cp /var/lib/jenkins/workspace/$JOB_NAME/target/ABCtechnologies-1.0.war 			   /var/lib/jenkins/workspace/$JOB_NAME/'
                sh "docker build -t amizak/addressbook:$BUILD_NUMBER ."
                sh "docker tag amizak/addressbook:$BUILD_NUMBER amizak/addressbook:$BUILD_NUMBER"
            }
        }

        stage ('Push Docker Image')
        {
            steps
            {
                withDockerRegistry([ credentialsId: 'dockercred', url: ""])
                {
                   sh 'docker push amizak/addressbook:$BUILD_NUMBER'
                }
            }
        }

        stage ('Deploy as container')
        {
            steps
            {
                sh 'docker run -itd -P amizak/addressbook:$BUILD_NUMBER'
            }
        }
  
    }
}

```
----
Application Access
The deployed application can be accessed via a web browser:
```bash
http://<Public_IP_VM>:<host_port>/ABCtechnologies-1.0
```
#### Outcome of running the ci-cd pipeline

<img width="1175" height="660" alt="Image" src="https://github.com/user-attachments/assets/b359811a-16d7-4fba-93e8-adc7e6c0f15c" />

<img width="1792" height="896" alt="Image" src="https://github.com/user-attachments/assets/c0aa963e-dc8e-47b5-ab79-3d04f24fa409" />

<img width="1215" height="566" alt="Image" src="https://github.com/user-attachments/assets/55792341-27f2-416f-8a3c-99fe1ba8eeae" />

<img width="1215" height="683" alt="Image" src="https://github.com/user-attachments/assets/176463bf-cde5-41c5-9432-e0c259b3dfa0" />

<img width="1215" height="719" alt="Image" src="https://github.com/user-attachments/assets/489bf186-e6cb-4a54-9718-0d6935aaeb3b" />


### Kubernetes Deployment – ABCtechnologies-1.0.war Application
#### Overview
The application is deployed on a MicroK8s Kubernetes cluster using a locally hosted container registry. The deployment runs a containerized Java application ABCtechnogies.war and exposes it internally within the cluster.

Before deploying confirm: 
microk8s is installed 
```bash
command -v microk8s
```
<img width="1100" height="760" alt="Image" src="https://github.com/user-attachments/assets/31a129a3-426c-4739-b416-6210c279c984" />

MicroK8s is running 
```bash
microk8s status
```
<img width="1429" height="872" alt="Image" src="https://github.com/user-attachments/assets/0ec7a566-c549-40b7-a78f-04d8e1749dae" />

Kubernetes API is reachable
```bash
microk8s kubectl get nodes
```
<img width="1429" height="872" alt="Image" src="https://github.com/user-attachments/assets/fb14243e-3ab3-46d0-914b-245a1f9cefeb" />

This checks:
1. API server
2. certificates
3. networking
4. permissions


Jenkins user has access to kubectl
```bash
ps aux | grep jenkins
```
<img width="1429" height="721" alt="Image" src="https://github.com/user-attachments/assets/c3ee00f3-7907-47d3-926c-663695e60a64" />

Verify group membership
```bash
groups jenkins
```
<img width="1229" height="271" alt="Image" src="https://github.com/user-attachments/assets/4cce4400-2db6-4673-b71b-47cb6e14b204" />

Run as Jenkins User
```bash
sudo -i -u jenkins
```
and

```bash
microk8s kubectl get pods -A
```

<img width="1816" height="874" alt="Image" src="https://github.com/user-attachments/assets/acfde4f5-576b-479a-90af-ba1931591e8e" />


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

<img width="1229" height="241" alt="Image" src="https://github.com/user-attachments/assets/4df14c0f-9e7b-4bce-a31e-cd86d30f4fb3" />

Check the deployment status:
```bash
microk8s kubectl get deployments
```

<img width="1713" height="460" alt="Image" src="https://github.com/user-attachments/assets/e6e717c8-4328-42c8-9525-8d7a93c55e61" />

Check running pods:
```bash
microk8s kubectl get pods
```
<img width="1713" height="138" alt="Image" src="https://github.com/user-attachments/assets/cdb7c655-ba24-4cb2-b334-3dbcb9c02530" />

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
<img width="1424" height="418" alt="Image" src="https://github.com/user-attachments/assets/f726b1c0-68cb-44ec-b879-7fa29aa06869" />

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

Outcome of deploying to kubernetes on jenkins

<img width="1764" height="1215" alt="Image" src="https://github.com/user-attachments/assets/f3df747c-0c3d-46a0-b2dd-65922b806298" />



### Author
#### Alek(YUSUF ALEAKHUE UMAR)








