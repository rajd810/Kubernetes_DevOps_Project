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

    stage ('Build Application') {
      steps {
        sh 'mvn clean package'
      }
    }

    stage ('Test Application') {
      steps {
        sh 'mvn test'
      }
    }
  }
}
