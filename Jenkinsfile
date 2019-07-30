pipeline {
  environment {
    registry = "pankajshukla3/jenkins-docker"
    /*registryCredential = 'dockerhub'*/
  }
  agent { dockerfile true }
  options {
    skipStagesAfterUnstable()
  }
  stages {
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
			bat 'node --version'
			bat 'svn --version'
		}
	}
	stage('Deploy') {
		steps {
			echo 'Deploying'
		}
	}
  }
}