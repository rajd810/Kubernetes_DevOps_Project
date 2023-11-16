pipeline {
  agent { label 'Jenkins-Agent' }
  tools {
    jdk 'Java17'
    maven 'Maven3'
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
        sh 'docker build —tag image-name .'
      }
    }

    stage ('Run Docker Image') {
      steps {
        sh 'docker run -d -p 5088:5088 image-name'
      }
    }
  }
}
