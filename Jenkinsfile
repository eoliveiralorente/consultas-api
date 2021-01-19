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
              git([url:'https://github.com/eoliveiralorente/consultas-api.git', branch:'main', credentialsId: 'eoliveiralorente_id']
            }           
          }
        }

        stage('Docker build') {
            steps {
                script {
                 sh "docker run -v /var/run/docker.sock:/var/run/docker.sock -ti docker"
                 sh "docker build -t eoliveiralorente/consulta-s3 ."   
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
