# Jenkins Shared Library Implementation

## DevOps Pipeline Reusability Project

This project demonstrates how to create and integrate a Jenkins Shared Library (JSL) in order to reuse common CI/CD pipeline logic across multiple Jenkins pipelines. Instead of duplicating pipeline code in every Jenkinsfile, reusable functions are stored in a separate repository and referenced by Jenkins pipelines.

The shared library allows teams to centralize common build logic such as building Java applications, running tests, and building Docker images. This approach improves maintainability, standardization, and scalability across multiple CI/CD pipelines.

---

## Technologies Used

Jenkins  
Groovy  
Git  
Docker  
Java  
Maven  

---

## Project Objectives

Create a separate Git repository for the Jenkins Shared Library  
Extract common CI/CD pipeline logic into reusable functions  
Use Groovy scripts to define pipeline functions  
Configure Jenkins to load the shared library globally  
Import the shared library inside Jenkins pipelines  
Use shared functions inside Jenkinsfile  

---

## Jenkins Shared Library Architecture

Developer → Jenkins Pipeline → Load Shared Library → Execute Shared Functions → Build Application

Workflow Explanation

1. Shared library is stored in a dedicated Git repository
2. Jenkins is configured to load the shared library
3. Jenkins pipeline imports the shared library
4. Pipeline calls reusable functions from the shared library
5. Functions execute tasks such as build, test, and Docker image creation

---

## Step 1: Create Jenkins Shared Library Repository

Create a new Git repository for the shared library.

Example repository name:

jenkins-shared-library

Clone the repository locally:

```
git clone https://github.com/yourusername/jenkins-shared-library.git
```

---

## Step 2: Create Shared Library Project Structure

The shared library must follow the standard Jenkins directory structure.

Example structure:

```
jenkins-shared-library
│
├── vars
│   └── buildApp.groovy
│
├── src
│
└── README.md
```

Explanation

vars → contains reusable pipeline functions  
src → optional directory for complex Groovy classes  

---

## Step 3: Create a Shared Library Function

Inside the vars directory create a Groovy file.

These functions can now be reused by any Jenkins pipeline.

---

## Step 4: Commit and Push Shared Library

```
git add .
git commit -m "Add Jenkins shared library functions"
git push origin main
```

---

## Step 5: Configure Shared Library in Jenkins (Global Library)

Open Jenkins Dashboard.

Navigate to:

Manage Jenkins → Configure System → Global Pipeline Libraries

Add a new library configuration.

Configuration example:

Library Name  
shared-library

Default Version  
main

Retrieval Method  
Modern SCM

Source Code Management  
Git

Repository URL  
https://github.com/yourusername/jenkins-shared-library.git

Save the configuration.

Now Jenkins can access the shared library globally.

---

## Step 6: Use Shared Library in Jenkins Pipeline

Inside a Jenkinsfile import the shared library.

Example Jenkinsfile:

```
@Library('shared-library') _

buildApp()
```

This will load the shared library and execute the buildApp function defined in the shared library.

---

## Step 7: Use Shared Library for a Specific Project

Instead of configuring globally, a shared library can also be loaded directly inside the Jenkinsfile.

---

## Example CI Workflow

1 Developer pushes code to repository  
2 Jenkins pipeline starts  
3 Jenkins loads the shared library  
4 Pipeline calls reusable functions from the library  
5 Application is built using Maven  
6 Docker image is created  

---

## Example Repository Structure

Application Repository

```
java-app-project
│
├── src
├── pom.xml
├── Dockerfile
├── Jenkinsfile
└── README.md
```

Shared Library Repository

```
jenkins-shared-library
│
├── vars
│   └── buildApp.groovy
│
├── src
│
└── README.md
```

---

## Benefits of Jenkins Shared Libraries

Eliminates duplicated pipeline code  
Improves maintainability of CI/CD pipelines  
Standardizes build and deployment processes  
Allows teams to reuse pipeline logic across projects  
Simplifies complex Jenkins pipelines  

---
