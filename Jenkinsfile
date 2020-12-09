pipeline {
  agent any
  stages {
    stage('build start') {
      steps {
        slackSend(message: "Build ${env.BUILD_NUMBER} Started", color: 'good', tokenCredentialId: 'slack-key')
      }
    }      
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
    
    stage('send diff') {
        steps {
        slackSend(message: """${env.JOB_NAME} #${env.BUILD_NUMBER} End
        """, color: 'good', tokenCredentialId: 'slack-key')             
        }
    }
    
  }
}
