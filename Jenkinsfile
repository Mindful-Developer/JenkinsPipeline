pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Mindful-Developer/JenkinsPipeline.git', branch: 'master'
            }
        }

        stage('Build Maven Project') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Docker Login') {
            steps {
                withCredentials([string(credentialsId: 'dockerhub-pwd', variable: 'dockerHubPwd')]) {
                    sh "docker login -u mindfuldeveloper -p ${dockerHubPwd}"
                }
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t mindfuldeveloper/welcome-comp367:latest .'
            }
        }

        stage('Docker Push') {
            steps {
                sh 'docker push mindfuldeveloper/welcome-comp367:latest'
            }
        }
    }
}