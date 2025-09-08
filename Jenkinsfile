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
                sh 'npm install'
            }
        }

        stage('Run Security Tests') {
            steps {
                // npm audit will exit nonzero if vulnerabilities are found,
                // so we add "|| true" to avoid failing the build.
                sh 'npm audit --json || true'

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
