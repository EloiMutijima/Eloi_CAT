
pipeline {
    agent any

    environment {
        CI = 'true'
    }

    stages {

        stage('Install Dependencies') {
            steps {
                echo 'Installing Juice Shop dependencies...'
                sh 'node --version'
                sh 'npm --version'
                sh 'CYPRESS_INSTALL_BINARY=0 npm install --no-audit --no-fund'
            }
        }

        stage('Build Application') {
            steps {                echo 'Building Juice Shop...'
                sh 'npm run build'
            }
        }

        stage('Automated Testing') {
            steps {
                echo 'Running automated server tests...'
                sh 'npm run test:server'
            }
        }
    }

    post {
        success {
            echo 'ELOI_CAT PIPELINE COMPLETED SUCCESSFULLY!'
        }

        failure {
            echo 'ELOI_CAT PIPELINE FAILED. CHECK THE LOGS.'
        }

        always {
            echo 'Jenkins pipeline execution finished.'
        }
    }
}
