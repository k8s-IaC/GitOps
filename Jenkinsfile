pipeline {
  agent any
  stages {      
    stage('git pull') {
        steps {
            // Please enter your git repository
            git url: 'https://github.com/k8s-IaC/GitOps', branch: 'main'
        }
    }
    stage('k8s deploy'){
        steps {
            kubernetesDeploy(kubeconfigId: 'kubeconfig',
                 configs: '*.yaml')
        }
    }    
  }
}
