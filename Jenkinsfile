pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Mindful-Developer/JenkinsPipeline.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
    }
}