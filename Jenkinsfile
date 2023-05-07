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
        success {
            println "Finished "
        }
    }
}
