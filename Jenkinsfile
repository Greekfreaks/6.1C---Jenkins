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
                // Simulating log output
                writeFile file: 'unit_tests.log', text: 'Sample log content for Unit and Integration Tests...'
            }
            post {
                always {
                    echo 'Archiving unit test logs...'
                    archiveArtifacts artifacts: 'unit_tests.log', allowEmptyArchive: true
                    echo 'Sending notification emails...'
                    emailext(
                        to: 'alucas.bros@gmail.com',
                        subject: "Pipeline Stage Completed: ${currentBuild.currentResult}",
                        body: """<p>Stage: ${env.STAGE_NAME}</p>
                                 <p>Status: ${currentBuild.currentResult}</p>""",
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
                // Simulating log output
                writeFile file: 'security_scan.log', text: 'Sample log content for Security Scan...'
            }
            post {
                always {
                    echo 'Archiving security scan logs...'
                    archiveArtifacts artifacts: 'security_scan.log', allowEmptyArchive: true
                    echo 'Sending notification emails...'
                    emailext(
                        to: 'alucas.bros@gmail.com',
                        subject: "Pipeline Stage Completed: ${currentBuild.currentResult}",
                        body: """<p>Stage: ${env.STAGE_NAME}</p>
                                 <p>Status: ${currentBuild.currentResult}</p>""",
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
}
