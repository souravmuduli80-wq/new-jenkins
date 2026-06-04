pipeline {
    agent any

    environment {
        EMAIL_TO = "souravmuduli80@gmail.com"
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Getting source code...'
            }
        }

        stage('Build') {
            steps {
                echo 'Building application...'
                bat 'javac Student.java'
            }
        }

        stage('Run') {
            steps {
                echo 'Running application...'
                bat 'java Student'
            }
        }
    }

    post {

        success {
            emailext(
                to: "souravmuduli80@gmail.com",
                subject: "SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: """
Build Status : SUCCESS

Job Name     : ${env.JOB_NAME}
Build Number : ${env.BUILD_NUMBER}
Build URL    : ${env.BUILD_URL}

The build completed successfully.
"""
            )
        }

        failure {
            emailext(
                to: "${EMAIL_TO}",
                subject: "FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: """
Build Status : FAILED

Job Name     : ${env.JOB_NAME}
Build Number : ${env.BUILD_NUMBER}
Build URL    : ${env.BUILD_URL}

Please check the Jenkins console logs.
"""
            )
        }
    }
}
