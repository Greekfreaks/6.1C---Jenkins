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
            }
            post {
                always {
                    script {
                        def logs = currentBuild.rawBuild.getLog(100).join("\n")
                        writeFile file: 'unit_tests.log', text: logs
                    }
                    echo 'Sending notification emails...'
                    emailext(
                        to: 'alucas.bros@gmail.com',
                        subject: "Pipeline Stage Completed: ${currentBuild.currentResult}",
                        body: "Stage: ${env.STAGE_NAME}\nStatus: ${currentBuild.currentResult}",
                        attachmentsPattern: 'unit_tests.log'
                    )
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
            }
            post {
                always {
                    script {
                        def logs = currentBuild.rawBuild.getLog(100).join("\n")
                        writeFile file: 'security_scan.log', text: logs
                    }
                    echo 'Sending notification emails...'
                    emailext(
                        to: 'alucas.bros@gmail.com',
                        subject: "Pipeline Stage Completed: ${currentBuild.currentResult}",
                        body: "Stage: ${env.STAGE_NAME}\nStatus: ${currentBuild.currentResult}",
                        attachmentsPattern: 'security_scan.log'
                    )
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

    post {
        always {
            echo 'Sending notification emails...'
            emailext(
                to: 'alucas.bros@gmail.com',
                subject: "Pipeline Stage Completed: ${currentBuild.currentResult}",
                body: "Stage: ${env.STAGE_NAME}\nStatus: ${currentBuild.currentResult}"
            )
        }
    }
}
