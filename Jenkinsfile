pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Use pip to install dependencies
                sh 'pip install -r requirements.txt'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration Tests...'
                // Use pytest for running tests
                sh 'pytest'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing Code...'
                // Use a tool like pylint for code analysis
                sh 'pylint src/*.py'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing Security Scan...'
                // Use a tool like Bandit for security scanning
                sh 'bandit -r src'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging...'
                // Deploy to staging server, e.g., using SCP or an automated deploy tool
                // sh 'scp src/*.py user@staging-server:/path/to/deploy'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on Staging...'
                // Run integration tests in staging environment
                // sh 'run-staging-tests.sh'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production...'
                // Deploy to production server
                // sh 'scp src/*.py user@production-server:/path/to/deploy'
            }
        }
    }
    post {
        always {
            echo 'Pipeline finished'
        }
        success {
            mail to: 'safymalik@yahoo.com',
                 subject: "Jenkins Pipeline Success: ${currentBuild.fullDisplayName}",
                 body: "The pipeline has succeeded."
        }
        failure {
            mail to: 'safymalik@yahoo.com',
                 subject: "Jenkins Pipeline Failed: ${currentBuild.fullDisplayName}",
                 body: "The pipeline has failed. Please check the logs."
        }
    }
}
