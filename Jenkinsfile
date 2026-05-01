pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Pulls the code from your GitHub repo
                checkout scm
            }
        }

        stage('Compile') {
            steps {
                // Compiles the code using Maven
                sh 'mvn clean compile'
            }
        }

https://github.com/cisco131185/java-jenkins-demo.git        stage('Run & Verify') {
            steps {
                // Executes the Java application
                // Note: exec.mainClass points to your App.java
                sh 'mvn exec:java -Dexec.mainClass="HelloWorld"'
            }
        }
    }
}

