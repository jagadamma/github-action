pipeline {
  agent any

  environment {
    COMPOSE_PROJECT_NAME = "myapp"
  }

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Build & Start Services') {
      steps {
        script {
          // Stop any existing containers
          sh 'docker-compose down'

          // Build images and start services
          sh 'docker-compose up -d --build'
        }
      }
    }

    stage('Verify Containers') {
      steps {
        sh 'docker ps -a'
      }
    }
  }

  
}
