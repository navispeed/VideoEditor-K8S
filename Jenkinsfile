pipeline {
  agent any
  stages {


    stage('Update API') {
      steps {
        withEnv(["API_TAG=${params.API}"]) {
          sh '''
           if [[ "${API_TAG}" == master-* ]]
           then
              cat api.yml | sed -r "s/master-[0-9]+/${API_TAG}/g" | microk8s.kubectl apply -f-     
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
              cat ui.yml | sed -r "s/master-[0-9]+/${UI_TAG}/g" | microk8s.kubectl apply -f-
           fi
           '''
        }
      }
    }
  }
}
