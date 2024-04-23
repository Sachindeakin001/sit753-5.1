pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                // Build the code using Maven
                sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                // Run unit tests using JUnit
                sh 'mvn test'
                // Run integration tests using Selenium
                sh 'npm install selenium-webdriver'
                sh 'node selenium-tests.js'
            }
        }
        stage('Code Analysis') {
            steps {
                // Integrate code analysis tool (e.g., SonarQube)
                sh 'sonar-scanner -Dsonar.projectKey=my-project'
            }
        }
        stage('Security Scan') {
            steps {
                // Perform security scan using a tool (e.g., OWASP ZAP)
                sh 'zap-cli --zap-url http://localhost:8080 --spider http://myapp.com --scan'
            }
        }
        stage('Deploy to Staging') {
            steps {
                // Deploy the application to staging server (e.g., AWS CodeDeploy)
                sh 'aws deploy --environment staging'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                // Run integration tests on staging environment
                sh 'run-integration-tests --environment staging'
            }
        }
        stage('Deploy to Production') {
            steps {
                // Deploy the application to production server (e.g., AWS CodeDeploy)
                sh 'aws deploy --environment production'
            }
        }
    }
}
