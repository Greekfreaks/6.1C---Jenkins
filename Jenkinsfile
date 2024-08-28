pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                // Build steps here
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration Tests...'
                // Unit test steps here
                script {
                    // Capture the logs
                    def unitTestLog = sh(script: 'cat unit_test_logs.txt', returnStdout: true).trim()
                    
                    // Send email with log included in the body
                    mail to: 'alucas.bros@gmail.com',
                         subject: "Pipeline Stage Completed: ${currentBuild.currentResult}",
                         body: """Stage: ${env.STAGE_NAME}
Status: ${currentBuild.currentResult}
Log:
${unitTestLog}
"""
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code quality...'
                // Code analysis steps here
            }
        }
        // Add more stages as necessary...
    }
}
