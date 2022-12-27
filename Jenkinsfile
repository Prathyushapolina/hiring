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
                withCredentials([string(credentialsId: 'docker-hub', variable: 'hubpwd')]) {
                    sh "docker login -u prathyushapolina -p ${hubpwd}"
                sh "docker push prathyushapolina/hiring:0.0.2"
               }
            }
        }
    }
}
