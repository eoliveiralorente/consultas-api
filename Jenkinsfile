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

        stage('build image s3') {
            steps {
                script {
                 sh docker build -f "Dockerfile -t eoliveiralorente/consulta-s3 ."   
              }
            }
        }
        
        stage('Deploy push imagem') {
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
