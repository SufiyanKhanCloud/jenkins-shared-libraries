# Jenkins Pipeline Scripts for Docker CI/CD

This repository contains a set of Groovy scripts designed to automate the CI/CD workflow using Jenkins and Docker. Each script performs a specific function in the pipeline—from cloning the repository to building and pushing Docker images.

## 📁 Repository Structure

- **`clone.groovy`**  
  Clones the source code repository from a specified Git URL into the Jenkins workspace.

- **`docker_build.groovy`**  
  Builds a Docker image from the source code using the provided `Dockerfile`.

- **`docker_push.groovy`**  
  Pushes the built Docker image to a container registry (e.g., Docker Hub or AWS ECR).

- **`hello.groovy`**  
  A simple "Hello, Jenkins!" script used for testing Jenkins Groovy pipeline steps.

## ⚙️ Usage

Integrate these scripts into your `Jenkinsfile` as shared library steps or load them directly using `load` if kept in the workspace.

Example usage in a Jenkins pipeline:

```groovy
stage('Clone Repository') {
    steps {
        load 'clone.groovy'
    }
}

stage('Build Docker Image') {
    steps {
        load 'docker_build.groovy'
    }
}

stage('Push Docker Image') {
    steps {
        load 'docker_push.groovy'
    }
}

stage('Hello World') {
    steps {
        load 'hello.groovy'
    }
}
