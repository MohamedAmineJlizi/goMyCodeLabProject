pipeline {
  // Equivalent to "docker build -f Dockerfile_angular -t angularImg .
  dockerfile {
    filename 'Dockerfile_angular'
    dir 'angular-app'
    additionalBuildArgs '-t angularImg'
  }

  environment {
    imagename1 = "expressImg"
    imagename1 = "angularImg"
    dockerImage1 = ''
    dockerImage2 = ''
  }
	
  agent any
	
  stages {
    stage('Building angular image') {
      steps{
        script {
          dockerImage1 = docker.build imagename1
        }
      }
    }
  }
}
