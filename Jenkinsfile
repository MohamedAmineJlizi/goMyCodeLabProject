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
          angular = docker.build(registry1,"-f ${env.WORKSPACE}/angular-app/Dockerfile .")
        }
      }
    }
    stage('Building express image') {
      steps{
        script {
          express = docker.build(registry2,"-f ${env.WORKSPACE}/express-server/Dockerfile .")
        }
      }
    }
	
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            angular.push(env.BUILD_ID)
            angular.push("latest")
          }
          docker.withRegistry( '', registryCredential ) {
            express.push(env.BUILD_ID)
            express.push("latest")
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
