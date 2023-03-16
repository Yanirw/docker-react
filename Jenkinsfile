pipeline {
    agent {
        docker {
            image 'node:12-alpine'
            args '-p 3000:3000'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'npm run test -- --coverage'
            }
        }
        stage('Deploy') {
            steps {
                sh 'npm run build'
            }
        }
    }
}

