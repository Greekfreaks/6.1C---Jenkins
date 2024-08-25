pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                echo 'Tool: Maven'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration Tests...'
                echo 'Tools: JUnit, TestNG'
                sh 'echo "Unit and Integration Tests logs..." > unit_integration_tests.log'
            }
            post {
                always {
                    echo 'Sending notification email for Unit and Integration Tests...'
                    mail to: 'alucas.bros@gmail.com',
                         subject: "Unit and Integration Tests Stage Completed: ${currentBuild.currentResult}",
                         body: "Stage: Unit and Integration Tests\nStatus: ${currentBuild.currentResult}",
                         attachmentsPattern: 'unit_integration_tests.log'
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyzing code quality...'
                echo 'Tool: SonarQube'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                echo 'Tool: OWASP ZAP'
                sh 'echo "Security Scan logs..." > security_scan.log'
            }
            post {
                always {
                    echo 'Sending notification email for Security Scan...'
                    mail to: 'your_email@example.com',
                         subject: "Security Scan Stage Completed: ${currentBuild.currentResult}",
                         body: "Stage: Security Scan\nStatus: ${currentBuild.currentResult}",
                         attachmentsPattern: 'security_scan.log'
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging server...'
                echo 'Deploying to AWS EC2 instance'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
                echo 'Integration Tests on Staging'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production server...'
                echo 'Deploying to AWS EC2 instance'
            }
        }
    }
}
