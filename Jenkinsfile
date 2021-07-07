pipeline {
  agent (label 'linux' }
  options {
    buildDiscarder (logRotator (numToKeepStr: '5'))
  }
  environment {
    DOCKERHUB CREDENTIALS = credentials('eddsnx3-dockerhub')
  }
  stages {
    stage('Build') {
	  steps {
	  sh 'docker build -t eddsnx3/my-site: latest.'
	  }
	}
	stage('Login') {
	  steps {
	    sh 'echo $DOCKERHUB CREDENTIALS PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR--password-stdin'
		}
	}
	stage('Push') {
	  steps {
	    sh 'docker push eddsnx3/my-site: latest'
	  }
	}
  }
  post {
    always {
	  sh 'docker logout'
	}
  }
}
