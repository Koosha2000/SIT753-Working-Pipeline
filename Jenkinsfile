pipeline {
    agent any

    triggers {
        pollSCM('H/2 * * * *')
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building with Maven...'
                echo 'Tool: Maven'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests...'
                echo 'Tools: JUnit, TestNG'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing with SonarQube...'
                echo 'Tool: SonarQube'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Scanning with OWASP Dependency-Check...'
                echo 'Tool: OWASP Dependency-Check'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging...'
                echo 'Tool: AWS CLI or Ansible'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Testing with Postman...'
                echo 'Tool: Postman'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production...'
                echo 'Tool: AWS CLI or Ansible'
            }
        }
    }
}
