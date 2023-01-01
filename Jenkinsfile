pipeline {
    agent any

    stages {
        
        stage('Maven Build') {
             steps {
                sh "mvn clean package"
            }
        }
        
        stage('Docker Build') {
            steps {
                sh "docker build -t prathyushapolina/hiring:0.0.2 ."
            }
        }
        stage('Docker Push') {
            steps {
                withCredentials([string(credentialsId:'docker-hub', variable:'hubpwd')]) {
                    sh "docker login -u prathyushapolina -p ${hubpwd}"
                sh "docker push prathyushapolina/hiring:0.0.2"
               }
            }
        }
         stage('Docker Deploy') {
            steps {
              sshagent(['docker-host']) {
                sh "ssh -o StrictHostKeyChecking=no ec2-user@172.31.34.186 docker run -d -p 8080:8080 --name hiring prathyushpolina/hiring:0.0.2"
             }
            }  
         } 
    }
}
