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
                // Simulate log creation for demonstration purposes
                writeFile file: 'unit_tests.log', text: 'Unit and Integration Tests log contents'
            }
            post {
                always {
                    echo 'Archiving unit test logs...'
                    archiveArtifacts artifacts: 'unit_tests.log', allowEmptyArchive: true
                    echo 'Sending notification emails...'
                    mail to: 'alucas.bros@gmail.com',
                         subject: "Pipeline Stage Completed: ${env.STAGE_NAME} - ${currentBuild.currentResult}",
                         body: "Stage: ${env.STAGE_NAME}\nStatus: ${currentBuild.currentResult}",
                         attachmentsPattern: 'unit_tests.log'
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
                // Simulate log creation for demonstration purposes
                writeFile file: 'security_scan.log', text: 'Security scan log contents'
            }
            post {
                always {
                    echo 'Archiving security scan logs...'
                    archiveArtifacts artifacts: 'security_scan.log', allowEmptyArchive: true
                    echo 'Sending notification emails...'
                    mail to: 'alucas.bros@gmail.com',
                         subject: "Pipeline Stage Completed: ${env.STAGE_NAME} - ${currentBuild.currentResult}",
                         body: "Stage: ${env.STAGE_NAME}\nStatus: ${currentBuild.currentResult}",
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
