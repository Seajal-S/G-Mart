pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Seajal-S/ECommerce-Website.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
        stage('Deploy') {
            steps {
                sh 'npm run deploy'
            }
        }
    }
}
