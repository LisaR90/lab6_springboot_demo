pipeline {
    agent any

    stages {
        stage('GetProject') {
            steps {
                git 'https://github.com/LisaR90/lab6_springboot_demo.git'
            }
        }
        stage('Build') {
            steps {
                sh "mvn clean:clean"

                sh "mvn dependency:copy-dependencies"

                sh "mvn compiler:compile"
            }
        }
        stage('Package') {
            steps {
            sh "mvn package"
            }
        }

        stage('Exec') {
            steps {
                sh "mvn exec:java"
            }
        }
    }
    post {
        success {
            archiveArtifacts allowEmptyArchive: true,
                artifacts:'**/demo_lab6_springboot_demo*.jar'
        }
    }
}