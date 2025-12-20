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

## Prerequisites

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

### Build Part 1: Jenkins & Maven Setup (Prerequisites)
#### Environment Setup

- **Virtualization Tool:** VirtualBox

- **Operating System:** Ubuntu Linux

**Installed Tools:** Jenkins, Maven, Git, Java (JDK)
