pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo "Build the code using Maven."
                echo "Compile and package the code."
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit tests using Katalon"
                echo "Running integration tests using Selenium"
            }
            post {
                always {
                    emailext(
                            subject: "Unit and Integration Tests - ${currentBuild.result}",
                            body: "Your build ${currentBuild.result}.",
                            attachmentsPattern: "${currentBuild.rawBuild.getLogFile().path}",
                            to: 'dotruongthanhan@egmail.com',
                            mimeType: 'text/plain'
                    )
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Analyse the code and ensure it meets industry standards using Sonar"
            }
        }
        stage('Security Scan') {
            steps {
                echo "Perform a security scan on the code using OWASP"
            }
            post {
                always {
                    emailext(
                            subject: "Security Scan - ${currentBuild.result}",
                            body: "Your build ${currentBuild.result}.",
                            attachmentsPattern: "${currentBuild.rawBuild.getLogFile().path}",
                            to: 'dotruongthanhan@egmail.com',
                            mimeType: 'text/plain'
                    )
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploy the application to an AWS EC2 server"
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Run integration tests on the staging environment using Citrus"
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploy the application to the AWS EC2 server"
            }
        }
    }
}
