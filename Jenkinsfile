pipeline {
  environment {
    registry1 = "aminejlizi/my-image-angular"
    registry2 = "aminejlizi/my-image-express"
    registryCredential = 'dockerhub'
    angular = ''
    express = ''

  }
  agent any
  stages {
    stage('Building angular image') {
      steps{
        script {
          def angular = docker.build(registry1+":${env.BUILD_ID}","-f ${env.WORKSPACE}/angular-app/Dockerfile .")
        }
      }
    }
    stage('Building express image') {
      steps{
        script {
          def express = docker.build(registry2+":${env.BUILD_ID}","-f ${env.WORKSPACE}/express-server/Dockerfile .")
        }
      }
    }
	
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( registry1, registryCredential ) {
            angular.push()
          }
          docker.withRegistry( registry2, registryCredential ) {
            express.push()
          }		
        }
      }
    }
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi my-image-angular"
        sh "docker rmi my-image-express"
      }
    }
  }
}
