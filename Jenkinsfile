pipeline {
  environment {
    registry = "docker_lab"
	registryCredential = 'dockerhub'

  }
  agent any
  stages {
    stage('Building angular image') {
      steps{
	    dir('/angular-app/'){
          script {
            docker.build registry + ":$BUILD_NUMBER"
          }
		}
      }
    }
    stage('Building express image') {
      steps{
	    dir('/express-server/'){
          script {
            docker.build registry + ":$BUILD_NUMBER"
          }
		}
      }
    }	
  }
}
