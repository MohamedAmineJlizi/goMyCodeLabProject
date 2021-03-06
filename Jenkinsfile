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
          angular = docker.build(registry1+":${env.BUILD_ID}","-f ${env.WORKSPACE}/angular-app/Dockerfile .")
        }
      }
    }
    stage('Building express image') {
      steps{
        script {
          express = docker.build(registry2+":${env.BUILD_ID}","-f ${env.WORKSPACE}/express-server/Dockerfile .")
        }
      }
    }
	
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            angular.push()
          }
          docker.withRegistry( '', registryCredential ) {
            express.push()
          }		
        }
      }
    }
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi "+registry1+":${env.BUILD_ID}"
        sh "docker rmi "+registry2+":${env.BUILD_ID}"
      }
    }
  }
}
