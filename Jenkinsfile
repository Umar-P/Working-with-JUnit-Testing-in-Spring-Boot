pipeline {
    agent {label 'slave'}
    environment {
    		DOCKERHUB_CREDENTIALS=credentials('docker-cred')
    	}
     tools {
            maven 'maven'
     }
    stages {
        stage('Pull latest code') {
            steps {
                git 'https://github.com/Umar-P/Working-with-JUnit-Testing-in-Spring-Boot'
            }
        }

        stage("Install") {
            steps {
                sh "mvn clean install"
            }
        }

        stage("Build a package") {
                    steps {
                        sh "mvn clean package"
                    }
                }

         stage("Test") {
                    steps {
                        sh "mvn test"
                    }
                }

         stage('Login To Docker Hub') {

         			steps {
         				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
         			}
         		}
    }
    post {
             always{
                        mail to: "mohamedumar931@gmail.com",
                        subject: "jenkins build:${currentBuild.currentResult}: ${env.JOB_NAME}",
                        body: "${currentBuild.currentResult}: Job ${env.JOB_NAME}\nMore Info can be found here: ${env.BUILD_URL}"
                    }
        }
}
