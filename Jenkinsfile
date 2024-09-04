pipeline {
    agent any

    environment {
        DIRECTORY_PATH = '/path/to/your/code'
        TESTING_ENVIRONMENT = 'TestingEnv'
        PRODUCTION_ENVIRONMENT = 'AmirProdEnv'
    }

    stages {
        stage('Build') {
            steps {
                echo "Building the code using Maven"
            }
        }

        stage('Test') {
            steps {
                echo "Running unit tests with JUnit and integration tests with Selenium"
            }
            post {
                always {
                    mail to: 'amirshakour6@gmail.com',
                         subject: "Test Stage: ${currentBuild.fullDisplayName}",
                         body: "Test stage completed with status: ${currentBuild.currentResult}\n\n${env.BUILD_URL}"
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo "Analyzing code quality with SonarQube"
            }
        }

        stage('Security Scan') {
            steps {
                echo "Scanning code for vulnerabilities with OWASP Dependency-Check"
            }
            post {
                always {
                    mail to: 'amirshakour6@gmail.com',
                         subject: "Security Scan Stage: ${currentBuild.fullDisplayName}",
                         body: "Security scan completed with status: ${currentBuild.currentResult}\n\n${env.BUILD_URL}"
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo "Deploying application to the staging server"
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests on staging with Selenium"
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Deploying application to the production server"
            }
        }
    }

    post {
        always {
            mail to: 'amirshakour6@gmail.com',
                 subject: "Pipeline: ${currentBuild.fullDisplayName}",
                 body: "Pipeline completed with status: ${currentBuild.currentResult}\n\n${env.BUILD_URL}"
        }
    }
}
