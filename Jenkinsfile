pipeline {
    agent any
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
    }
    post {
        success {
            println "Finished "
        }
    }
}
