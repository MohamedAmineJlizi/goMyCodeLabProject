pipeline {
  environment {
    angularRegistry = "angular-app"
    expressRegistry = "express-server"

  }
  agent any
  stages {
    stage('Building angular image') {
      steps{
        script {
          docker.build angularRegistry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Building express image') {
      steps{
        script {
          docker.build expressRegistry + ":$BUILD_NUMBER"
        }
      }
    }	
  }
}
