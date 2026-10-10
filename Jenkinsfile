
pipeline {
    agent any

    tools {
        jdk 'JDK_21'
        maven 'Maven3'
    }

    stages {
        stage('Check Java and Maven') {
            steps {
                bat 'java -version'
                bat 'mvn -version'
            }
        }

        stage('Checkout Source') {
            steps {
                checkout scm
            }
        }

        stage('Run TestNG Tests') {
            steps {
                bat 'mvn clean test'
            }
        }
    }

    post {
        always {
            junit allowEmptyResults: true,
                  testResults: '**/target/surefire-reports/*.xml'
        }
    }
}
