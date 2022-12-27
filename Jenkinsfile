pipeline {
    agent any

    stages {
        
        stage('Maven Build') {
             steps {
                sh "mvn clean package"
            }
        }
        
        stage('Docker build' {
            steps {
                sh "docker build -t prathyushapolina/hiring:0.0.2 ."
            }
        }
        stage('Docker push') {
            steps {
               sh "docker login -u prathyushapolina -p xxxxxxx"
                sh "docker push prathyushapolina/hiring:0.0.2"
            }
        }
    }
}
