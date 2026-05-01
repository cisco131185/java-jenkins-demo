pipeline {
    agent any

    tools {
        // This must match the 'Name' you gave Maven in Manage Jenkins -> Tools
        maven 'maven_3' 
    }

    stages {
        stage('Compile') {
            steps {
                echo 'Compiling the Java application...'
                // Clean removes old build files, compile generates the .class files
                sh 'mvn clean compile'
            }
        }

        stage('Run & Verify') {
            steps {
                echo 'Executing the application...'
                // Using the Maven Exec plugin to run the main class
                sh 'mvn exec:java -Dexec.mainClass="HelloWorld"'
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
