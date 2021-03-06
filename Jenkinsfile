pipeline {
  environment {
    registry = "https://api.github.com/aminejlizi/docker_lab"
    registryCredential = "dockerhub"

  }
  agent any
  stages {
    stage('Building angular image') {
      steps{
        script {
          def angular = docker.build("my-image-angular:${env.BUILD_ID}","-f ${env.WORKSPACE}/angular-app/Dockerfile .")
        }
      }
    }
    stage('Building express image') {
      steps{
        script {
          def express = docker.build("my-image-express:${env.BUILD_ID}","-f ${env.WORKSPACE}/express-server/Dockerfile .")
        }
      }
    }
	
    stage('Deploy images') {
      steps{
        script {
          docker.withRegistry( registry, registryCredential ) {
            angular.push()
            express.push()
          }
        }
      }
    }
    stage('Remove unused docker images') {
      steps{
        sh "docker rmi my-image-angular"
        sh "docker rmi my-image-express"
      }
    }
  }
}
