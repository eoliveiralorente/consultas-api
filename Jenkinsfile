pipeline {
  agent any
  stages {
    stage('Clonar') {
      steps {
        git(url: 'https://github.com/eoliveiralorente/consultas-api.git', branch: 'main', credentialsId: 'eoliveiralorente_id')
      }
    }

  }
}