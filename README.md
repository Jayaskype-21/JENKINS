# JENKINS

#email notification for jenkins
pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
    }

    post {
        failure {
            emailext(
                body: 'Oops! Your job has failed.',
                subject: 'Build Failure',
                to: 'jayasree7903@gmail.com'
            )
        }
        success {
            emailext(
                body: 'Wow! Your job succeeded 🎉',
                subject: 'Build Success',
                to: 'jayasree7903@gmail.com'
            )
        }
    }
}
