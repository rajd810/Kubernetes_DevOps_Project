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
    IMAGE_NAME = "rajd810" + "/" + "${APP_NAME}"
    IMAGE_TAG = "${RELEASE}-${BUILD_NUMBER}"
    registry = "<dockerhub-username>/<repo-name>"
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

    stage ('Build Docker Image') {
      steps {
        script {
          //sh 'docker build -t "${IMAGE_NAME}" .'
          echo "Passing to next steps"
        }
      }
    }

    stage ('Docker Login') {
      steps {
        script {
          sh 'echo $DOCKERHUB_CREDENTIALS_PSW | sudo docker login -u $DOCKER_PASS --password-stdin aws_account_id.dkr.ecr.region.amazonaws.com'
        }
      }
    }
  }
}
