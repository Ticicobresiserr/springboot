pipeline {

    agent any

    stages {
        stage('Build') {
            steps {

                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [[$class: 'CleanCheckout']], userRemoteConfigs: [[credentialsId: 'credenciales_git_2', url: 'https://github.com/Ticicobresiserr/springboot.git']]])
                sh "echo 'github 1'"
                sh "docker build ."
                // sh "mvn clean package springboot:repackage "

            }

        }
    }
}
