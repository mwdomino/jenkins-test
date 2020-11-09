pipeline {
  agent any
  environment {
    APPLICATION = 'app'
    ENVIRONMENT = 'dev'
    MAINTAINER_NAME = 'jenkins'
    MAINTAINER_EMAIL = 'jenkins@email.com'
  }

  stages {
    stage('clone repository') {
      steps {
        checkout scm
      }
    }

    stage('Build Image') {
      steps {
        script {
          sshagent(credentials : ['matt-mbp-ssh-key']) {
            sh "echo pwd"
            sh "ssh -tt root@172.99.75.16 -o StrictHostKeyChecking=no touch /root/i_wuz_here"
          }
        }
      }
    }
  }
}
