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
                success {
                    mail to: "dotruongthanhan@gmail.com",
                    subject: "[SIT223] Unit and Integration Tests Result",
                    body: "Unit and Integration Tests succeeded"
                }
                failure {
                    mail to: "dotruongthanhan@gmail.com",
                    subject: "[SIT223] Unit and Integration Tests Result",
                    body: "Unit and Integration Tests - failed"
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
                success {
                    mail to: "dotruongthanhan@gmail.com",
                    subject: "[SIT223] Security Scan Result",
                    body: "Security Scan succeeded"
                }
                failure {
                    mail to: "dotruongthanhan@gmail.com",
                    subject: "[SIT223] Security Scan Result",
                    body: "Security Scan failed"
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
