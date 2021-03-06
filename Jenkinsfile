pipeline {
  environment {
    registry = "docker_lab"
	registryCredential = 'dockerhub'

  }
  agent any
  stages {
    stage('Building angular image') {
      steps{
        script {
          def angular = docker.build("my-image:${env.BUILD_ID}","-f ${env.WORKSPACE}/angular-app/Dockerfile .")
        }
      }
    }
    stage('Building express image') {
      steps{
        script {
          def express = docker.build("my-image:${env.BUILD_ID}","-f ${env.WORKSPACE}/express-server/Dockerfile .")
        }
      }
    }
  }
}
