pipeline {
  environment {
    registry = "pankajshukla3/jenkins-docker"
    registryCredential = 'dockerhub'
  }
  /*agent { dockerfile true }*/
  agent any
  options {
    skipStagesAfterUnstable()
  }
  stages {
    /*stage('Cloning Git') {
      steps {
        git 'https://github.com/pankajshukla3/jenkins-docker.git'
      }
    }*/
    stage('Building image') {
      steps{
        script {
          docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
	stage('Build') {
		steps {
			echo 'Building'
		}
	}
	stage('Test') {
		steps {
			echo 'Testing'
		}
	}
	stage('Deploy') {
		steps {
			echo 'Deploying'
		}
	}
  }
}
