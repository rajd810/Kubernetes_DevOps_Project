pipeline {
  agent { label 'Jenkins-Agent' }
  tools {
    jdk 'Java17'
    maven 'Maven3'
  }
  environment {
    APP_NAME = "kubernetes_devops_project"
    RELEASE = "1.0.0"
    DOCKER_USER = "rajd810@outlook.com"
    DOCKER_PASS = "docker"
    IMAGE_NAME = "${DOCKER_USER}" + "/" + "${APP_NAME}"
    IMAGE_TAG = "${RELEASE}-${BUILD_NUMBER}"
  }

  stages {
    stage ('Cleanup Workspace') {
      steps {
        cleanWs()
      }
    }

    stage ('Checkout from SCH') {
      steps {
        git branch: 'main', credentialsId: 'github', url: 'https://github.com/rajd810/Kubernetes_DevOps_Project.git'
      }
    }

    stage ('Build & Push Docker Image') {
      steps {
        sh 'docker build -t '
      }
    }
  }
}
