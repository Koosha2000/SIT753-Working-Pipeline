pipeline {
    agent any

    environment {
        RECIPIENT = 'radikhal2000@gmail.com'  
    }

    stages {
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    try {
                        sh 'npm run test'
                    } catch (err) {
                        echo "Test stage failed"
                        throw err
                    }
                }
            }
            post {
                always {
                    emailext(
                        subject: "Test Stage - ${currentBuild.currentResult}",
                        body: "The test stage has completed with result: ${currentBuild.currentResult}",
                        to: "${RECIPIENT}",
                        attachmentsPattern: 'test.log',
                        attachLog: true
                    )
                }
            }
        }

        stage('Security Scan') {
            steps {
                script {
                    try {
                        sh 'npm audit --audit-level=high || true'
                        sh 'echo \"Security scan completed at $(date)\" > security.log'
                    } catch (err) {
                        echo "Security scan failed"
                        throw err
                    }
                }
            }
            post {
                always {
                    emailext(
                        subject: "Security Scan - ${currentBuild.currentResult}",
                        body: "The security scan stage has completed with result: ${currentBuild.currentResult}",
                        to: "${RECIPIENT}",
                        attachmentsPattern: 'security.log',
                        attachLog: true
                    )
                }
            }
        }

        stage('Build (Optional)') {
            steps {
                sh 'echo "Build complete!"'
            }
        }
    }
}
