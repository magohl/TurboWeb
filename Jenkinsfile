pipeline {
  environment {
    registry = "docker_hub_account/repository_name"
    registryCredential = 'dockerhub'
  }
  agent any
  stages {
    stage('Building image') {
      steps{
        script {
         sh "docker build -t magohl/turboweb" + ":$BUILD_NUMBER" + " ."
        }
      }
    }
        stage('Push image') {
      steps{
        script {
            withDockerRegistry([ credentialsId: "077a7e77-6109-4dd3-b6e7-5bff8d65662b", url: "" ]) {
                 sh "docker push magohl/turboweb" + ":$BUILD_NUMBER"
             }
        }
      }
    }

  }
}