pipeline {
  agent any
  stages {


    stage('Update API') {
      steps {
        withEnv(["API_TAG=${params.API}"]) {
          sh '''
           if [ "${API_TAG}" != "" ]
           then
              cat api.yml | sed -r 's/master-[0-9]+/master-${API-TAG}/g' | microk8s.kubectl apply -f-
           else
              microk8s.kubectl apply -f api.yml           
           fi
           '''
        }
      }
    }

    stage('Update UI') {
      steps {
        withEnv(["UI_TAG=${params.UI}]"]) {
          sh '''
           if [ "${UI_TAG}" != "" ]
           then
              cat ui.yml | sed -r 's/master-[0-9]+/master-${UI-TAG}/g' | microk8s.kubectl apply -f-
           else
              microk8s.kubectl apply -f ui.yml           
           fi
           '''
        }
      }
    }
  }
}
