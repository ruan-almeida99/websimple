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
          // Obter a lista de containers que estão parados
          def containers = sh(script: 'docker ps -a -q --filter name=my-nginx', returnStdout: true).trim()

          // Verificar se há containers e parar e remover se houver
          if (containers) {
              sh "docker stop ${containers} && docker rm ${containers}"
          }

          sh "docker run -d -p 8000:80 --name my-nginx my-nginx:${env.BUILD_ID}"
        }
      }
    }
  }
}
