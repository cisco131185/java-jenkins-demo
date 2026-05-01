pipeline {
	agent any

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

		stage('Remove Old Container') {
			steps {
				echo 'Removing old container if exists...'
				sh 'docker rm -f java-container || true'
			}
		}

		stage('Run Docker Container') {
			steps {
				echo 'Running Docker container...'
				sh 'docker run --name java-container java-app'
			}
		}

		stage('Verify Output') {
			steps {
				echo 'Checking container logs...'
				sh 'docker logs java-container'
			}
		}
	}

	post {
		success {
			echo 'Pipeline completed successfully!'
		}
		failure {
			echo 'Pipeline failed. Check logs.'
		}
	}
}
