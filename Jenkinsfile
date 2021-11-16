pipeline {
    
    environment { 
        registryCredential = 'dockerhub_id' 
        dockerImage = "ticicobresiserr/spring-boot:"
        ver= ''
        
    }

    agent any

    stages {
        stage('Build') {
            steps {

                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [[$class: 'CleanCheckout']], userRemoteConfigs: [[credentialsId: 'credenciales_git_2', url: 'https://github.com/Ticicobresiserr/springboot.git']]])
                sh "echo 'github 1'"
                sh "docker build -t test-spring-boot ."
                // sh "mvn clean package springboot:repackage "

            }

        }
        
        stage('Publish') { 
            steps { 
                script { 
                    ver = "v1.0." + "$BUILD_NUMBER" 
                    sh "echo $ver"
                    dockerImage = dockerImage + ver
                    
                    docker.withRegistry( '', registryCredential ){
                        sh "docker tag test-spring-boot:latest $dockerImage"
                        
                        sh "docker push $dockerImage"
                    }
                } 
                
            
            }
        }
    }
}
