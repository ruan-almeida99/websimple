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
  }
}
