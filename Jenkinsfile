pipeline {
    agent any

    stages {
        stage('Compile') {
            steps {
                echo 'Compiling the Java application...'
      
                sh 'javac HelloWorld.java'
            }
        }

        stage('Run & Verify') {
            steps {
                echo 'Executing the application...'
		sh 'java HelloWorld'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the console output above for errors.'
        }
    }
}
