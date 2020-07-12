pipeline {
  agent any
  stages {
    stage('Update API') {
      steps {
        withEnv(["API_TAG=${params.API}"]) {
          sh '''
           if [[ "${API_TAG}" == master-* ]]
           then
              microk8s.helm3 upgrade editor-api api/ --set-string image.tag=${API_TAG}
           fi
           '''
        }
      }
    }

    stage('Update UI') {
      steps {
        withEnv(["UI_TAG=${params.UI}"]) {
          sh '''
           if [[ "${UI_TAG}" == master-* ]]
           then
              microk8s.helm3 upgrade editor-ui ui/ --set-string image.tag=${UI_TAG}
           fi
           '''
        }
      }
    }
  }
}
