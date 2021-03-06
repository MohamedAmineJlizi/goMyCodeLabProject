pipeline {
  environment {
    registry = "docker_lab"
	registryCredential = 'dockerhub'

  }
  agent any
  stages {
    stage('Building angular image') {
      steps{
        def angular = docker.build("my-image:${env.BUILD_ID}","-f ${env.WORKSPACE}/angular-app/Dockerfile registry + :$BUILD_NUMBER")
      }
    }
    stage('Building express image') {
      steps{
        def express = docker.build("my-image:${env.BUILD_ID}","-f ${env.WORKSPACE}/express-server/Dockerfile registry + :$BUILD_NUMBER")
      }
    }
  }
}
