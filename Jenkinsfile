pipeline {
  agent any
  
    stages {
      stage('Docker Build') {
      agent any
      steps {
        sh 'docker build -t avis2good/blessed:latest .'
      }
    }
    stage('Docker Push') {
      agent any
      steps {
        withCredentials([usernamePassword(credentialsId: 'docker_hub_login', passwordVariable: 'docker_hub_loginPassword', usernameVariable: 'docker_hub_loginUser')]) {
          sh "docker login -u ${env.docker_hub_loginUser} -p ${env.docker_hub_loginPassword}"
          sh 'docker push avis2good/blessed:latest'
        }
      }
    }
       
}
} 
