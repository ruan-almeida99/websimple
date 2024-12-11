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
          sh "docker stop my-nginx"
          sh "docker rm my-nginx"
          sh "docker run -d -p 8000:80 --name my-nginx my-nginx:${env.BUILD_ID}"
        }
      }
    }
  }
}
