pipeline {
  environment {
    registry = "pankajshukla3/jenkins-docker"
    registryCredential = 'dockerhub'
	dockerImage = ''
  }
  /*agent { dockerfile true }*/
  agent any
  options {
    skipStagesAfterUnstable()
  }
  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/pankajshukla3/jenkins-docker.git'
      }
    }
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $registry:$BUILD_NUMBER"
      }
    }
  }
}
