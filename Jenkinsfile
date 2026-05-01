pipeline {
	agent any
	
	environment {
		DOCKER_IMAGE = 'ditiss131185/java-app'
	}

	stages {

		stage('Clone Repo') {
			steps {
				git branch: 'main', url: 'https://github.com/cisco131185/java-jenkins-demo.git'
			}
		}

		stage('Build Docker Image') {
			steps {
				echo 'Building Docker Image...'
				sh 'docker build -t java-app .'
			}
		}
		
		stage('tag image') {
			steps {
				sh 'docker tag java-app $DOCKER_IMAGE:latest'
			}
		}
		
		stage('login to dockerhub') {
			steps {
				withCredentials([usernamePassword(credentialsId: 'dockerhub-cred', usernameVariable: 'USER', passwordVariable: 'PASS'))
				sh 'echo $PASS | docker login -u $USER --password-stdin'
			}
		}	

		stage('push image') {
			steps {
				sh 'docker push $DOCKER_IMAGE:latest'
			}
		}

	}

	post {
		success {
			echo 'docker image pushed successfully!'
		}
		failure {
			echo 'Pipeline failed. Check logs.'
		}
	}
}
