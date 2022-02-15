pipeline {
    agent any
    environment {
   ANSIBLE_PRIVATE_KEY=credentials('ansible-key') 
  }
    /*
    agent {
        docker { image 'sravangcpdocker/terraform:7' }
    }*/
    stages {
        stage('git-clone') {
            steps {
                sh '''
                   #!/bin/bash
                   git clone https://github.com/sravan-github/ansible.git
                   ls -ltr
                   '''
            }
        }
        stage('playbook') {
            steps {
                sh '''
                #!/bin/bash
                #ansible-playbook play.yml
                ansible-playbook --private-key=$ANSIBLE_PRIVATE_KEY play.yml
                '''
            }
          }
        
    }

post {
        always {
            cleanWs deleteDirs: true
        }
     }
}
