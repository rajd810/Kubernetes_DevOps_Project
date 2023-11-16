pipeline {
  agent { label 'Jenkins-Agent' }
  tools {
    jdk 'Java17'
    maven 'Maven3'
  }
  environment {
    APP_NAME = "kubernetes_devops_project"
    RELEASE = "2.0.0"
    DOCKER_USER = "rajd810@outlook.com"
    DOCKER_PASS = "docker"
    IMAGE_NAME = "devops" + "/" + "${APP_NAME}"
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
        script {
            docker.withRegistry('',DOCKER_PASS) {
            docker_image = docker.build "${IMAGE_NAME}"
          }
            docker.withRegistry('', DOCKER_PASS) {
            docker_image.push("${IMAGE_TAG}")
            docker_image.push('latest')
          }
        }
      }
    }
  }
}
