pipeline {
environment {
    registry = "eoliveiralorente/consulta-s3"
    registryCredential = 'dockerhub_id'
    dockerImage = ''
}
    agent any
    
        stages {
            
        stage('Clonar git') {
          steps {
            script {
              git([url:'https://github.com/eoliveiralorente/consultas-api.git', branch:'main', credentialsId: 'eoliveiralorente_id']) 
            }           
          }
        }

        stage('Docker build') {
            steps {
                script {
                 sh docker build -f "Dockerfile ."   
              }
            }
        }
        
        stage('Docker push') {
            steps {
                script {
                docker.withRegistry('https://registry.hub.docker.com',registryCredential ) {
                dockerImage.push()
                }
            }
        }
        
       }
    }
}
