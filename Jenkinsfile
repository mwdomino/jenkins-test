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
            sh '''
              ssh -t -t root@172.99.75.160 'bash -s << 'ENDSSH'
                docker stop nginx
                docker rm nginx
                docker run -d --rm nginx
        ENDSSH'
        ''''
          # ssh to opsbox
          # docker stop opapp
          # docker rm opapp
          # git clone
          # docker build opapp
          # docker run opapp
#            sh "echo pwd"
#            sh "ssh -tt root@172.99.75.160 -o StrictHostKeyChecking=no touch /root/i_wuz_here"
          }
        }
      }
    }
  }
}
