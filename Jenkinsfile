pipeline {
  agent any
  stages {
    stage('Update API') {
      steps {
        sh 'microk8s.kubectl apply -f api.yml'
      }
    }

    stage('Update UI') {
      steps {
        sh 'microk8s.kubectl apply -f ui.yml'
      }
    }
  }
}
