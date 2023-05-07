void sendBuildFailedEmail(){
if(currentBuild.currentResult!="SUCCESS"){
    String emailSubject  = "Jenkins-${app_env} backend build #${BUILD_NUMBER} Failed"
    emailext to: 'mohamedumar931@gmail.com',
    subject: emailSubject,
    body: "See build log here - ${BUILD_URL}"
    }
}

void sendBuildStatusChangedEmail(){
    if(currentBuild.currentResult=="SUCCESS"){
        String emailSubject  = "Jenkins-${app_env} backend build #${BUILD_NUMBER} is now passing"
        emailext to: 'mohamedumar931@gmail.com',
        subject: emailSubject,
        body: "See build log here - ${BUILD_URL}"
    }
}

pipeline {
    agent {label 'slave'}
     tools {
            maven 'maven'
     }
    stages {
        stage('Pull latest code') {
            steps {
                git 'https://github.com/Umar-P/Working-with-JUnit-Testing-in-Spring-Boot'
            }
        }

        stage("Build") {
            steps {
                sh "mvn clean install"
            }
        }

         stage("Test") {
                    steps {
                        sh "mvn test"
                    }
                }
    }
    post {
            failure {
                sendBuildFailedEmail()
            }
            changed {
                sendBuildStatusChangedEmail()
            }
            success {
                println "Finished "
            }
        }
}
