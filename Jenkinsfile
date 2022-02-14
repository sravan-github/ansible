pipeline {
    //agent any
    
    agent {
        docker { image 'sravangcpdocker/terraform:7' }
    }
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
                chmod +x play.yml
                ansible-playbook -vvv play.yml
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
