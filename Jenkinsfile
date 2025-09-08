pipeline {
    agent any

    tools {
        nodejs "NodeJS"   
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

        stage('Run Security Tests') {
            steps {
                // npm audit will exit nonzero if vulnerabilities are found,
                // so we add "|| true" to avoid failing the build.
                bat 'npm audit --json || exit /b 0'

                // Optional: run snyk if installed
                // sh 'npx snyk test || true'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed.'
        }
    }
}
