pipeline {
    agent any
    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/G-0nE007/ABA.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-app .'
            }
        }
        stage('Run Container') {
            steps {
                sh 'docker run -d -p 5000:5000 flask-app'
            }
        }
        stage('Notify Slack') {
            steps {
                slackSend(channel: '#ci-cd-notifications', message: 'Build and deployment successful!')
            }
        }
    }
}