pipeline {
    agent any

    tools {
        nodejs "NodeJS"  // Must match the name in Global Tool Configuration
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Sherinannasajeev/8.2CDevSecOps.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'npm test || exit /b 0' // Continue despite test failures
            }
        }

        stage('Generate Coverage Report') {
            steps {
                bat 'npm run coverage || exit /b 0' // Ensure coverage report exists
            }
        }

        stage('NPM Audit (Security Scan)') {
            steps {
                bat 'npm audit || exit /b 0' // Show known CVEs without failing pipeline
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed.'
        }
    }
}
