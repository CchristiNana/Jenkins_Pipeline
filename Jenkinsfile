pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Maven could be used as a build automation tool here.
                echo "Building with Maven..."
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                // JUnit for unit testing, and Selenium for integration testing could be used here.
                echo "Running unit tests with JUnit and integration tests with Selenium..." 
            }
            post {
        success {
            script {
                // Store the console log in a variable
                def consoleLog = Jenkins.instance.getItemByFullName(env.JOB_NAME).getBuildByNumber(env.BUILD_NUMBER).logFile.text
                // Write the console log to a file
                writeFile(file: "unit_integration_tests.log", text: consoleLog)
            }
            emailext (
                to: "cccccsy126@gmail.com",
                subject: "SUCCESS: Unit and Integration Tests",
                body: "The Unit and Integration Tests have passed successfully.",
                attachmentsPattern: "unit_integration_tests.log"
            )
        }
        failure {
            script {
                // Store the console log in a variable
                def consoleLog = Jenkins.instance.getItemByFullName(env.JOB_NAME).getBuildByNumber(env.BUILD_NUMBER).logFile.text
                // Write the console log to a file
                writeFile(file: "unit_integration_tests.log", text: consoleLog)
            }
            emailext (
                to: "cccccsy126@gmail.com",
                subject: "FAILURE: Unit and Integration Tests",
                body: "The Unit and Integration Tests have failed. Please review the attached log for more details.",
                attachmentsPattern: "unit_integration_tests.log"
            )
        }
        stage('Code Analysis') {
            steps {
                // SonarQube could be used for static code analysis.
                echo "Analyzing code with SonarQube..."
            }
        }
        stage('Security Scan') {
            steps {
                // Synopsys could be used for security scanning.
                echo "Scanning security with Synopsys..."
            }
        }
        stage('Deploy to Staging') {
            steps {
                // AWS EC2 instance could be used for deployment.
                echo "Deploying to staging server with AWS EC2 instance..."
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                // Selenium could be used again to run integration tests on the staging environment.
                echo "Running integration tests on staging with Selenium..."
            }
        }
        stage('Deploy to Production') {
            steps {
                // AWS EC2 instance could be used for deployment.
                echo "Deploying to production server with AWS EC2 instance..."
            }
        }
    }
}