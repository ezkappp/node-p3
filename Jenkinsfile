pipeline {
    agent any
    tools {
        nodejs 'NodeJS 16'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/USERNAME/node.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
            post {
                success { junit 'test-results.xml' }
                failure { echo 'Tests failed!' }
            }
        }
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying to production environment...'
            }
        }
    }
    post {
        success { echo 'Pipeline completed successfully!' }
        failure  { echo 'Pipeline failed!' }
    }
}
