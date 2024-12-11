pipeline {
  agent any

  stages {
    stage ('Build') {
       steps {
         script {
          docker.build("my-nginx:${env.BUILD_ID}")
         }
       }
    }
    stage ('Deploy') {
      steps {
        script {
          sh "docker run -d -p 8000:80 my-nginx:${env.BUILD_ID}"
        }
      }
    }
  }
}
