pipeline {
    agent any
    stages {
        stage('Send Test Email') {
            steps {
                emailext(
                    to: 'alucas.bros@gmail.com',
                    subject: 'Test Email from Jenkins',
                    body: 'This is a test email to check the system.',
                )
            }
        }
    }
}
