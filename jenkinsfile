pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven.' 
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests with JavaUnit...' 
                echo 'Running integration tests with Selenium...' 
            }
            post {
                success {
                    mail to: "fernandojanuda@gmail.com",
                         subject: "Tests Passed - Build # ${currentBuild.number}",
                         body: "Unit and integration tests have successfully completed. Build logs are attached.",
                         attachLog: true
                }
                failure {
                    mail to: "fernandojanuda@gmail.com",
                         subject: "Tests Failed - Build # ${currentBuild.number}",
                         body: "Unit and integration tests have failed. Build logs are attached.",
                         attachLog: true
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code quality with SonarQube...' 
            }
            post {
                success {
                    mail to: "fernandojanuda@gmail.com",
                         subject: "Code Analysis Passed - Build # ${currentBuild.number}",
                         body: "Code analysis has completed successfully. Build logs are attached.",
                         attachLog: true
                }
                failure {
                    mail to: "fernandojanuda@gmail.com",
                         subject: "Code Analysis Failed - Build # ${currentBuild.number}",
                         body: "Code analysis has failed. Build logs are attached.",
                         attachLog: true
                }
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Scanning for vulnerabilities with SAST scanner..'
            }
            post {
                success {
                    mail to: "fernandojanuda@gmail.com",
                         subject: "Security Scan Passed - Build # ${currentBuild.number}",
                         body: "Security scan has successfully completed. Build logs are attached.",
                         attachLog: true
                }
                failure {
                    mail to: "fernandojanuda@gmail.com",
                         subject: "Security Scan Failed - Build # ${currentBuild.number}",
                         body: "Security scan has failed. Build logs are attached.",
                         attachLog: true
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying application to staging server using AWS..'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging environment...'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying application to production server using AWS tools..'
            }
        }
    }
  
    post {
        success {
            mail to: "fernandojanuda@gmail.com",
                 subject: "Pipeline Success - Build # ${currentBuild.number}",
                 body: "The pipeline has successfully completed all stages. Build logs are attached.",
                 attachLog: true
        }
        failure {
            mail to: "fernandojanuda@gmail.com",
                 subject: "Pipeline Failure - Build # ${currentBuild.number}",
                 body: "The pipeline has failed at stage ${currentStage.name}. Build logs are attached.",
                 attachLog: true
        }
    }
}
