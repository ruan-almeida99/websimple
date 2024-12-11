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
          sh "if [[ $(docker ps -a -q | wc -m) -gt 0 ]]; then   docker stop $(docker ps -a -q) && docker rm $(docker ps -a -q); fi"
          sh "docker run -d -p 8000:80 --name my-nginx my-nginx:${env.BUILD_ID}"
        }
      }
    }
  }
}
