pipeline {
    agent any
    
    stages {
        stage('Puppet Apply') {
            environment{
                ENV = 'staging'
            }
            steps {
                echo 'Git Pull'
                   sh ''' 
                        cd /opt/ansible-scripts/
                        ansible-playbook -i staging git_pull.yaml --extra-vars "node=puppet-master"
                   '''      
            }
            steps {
                echo 'Run Ansible Scripts'
                  sh '''
                        cd /opt/ansible-scripts/
                        ansible-playbook -i staging puppet_apply.yaml --extra-vars "node=identity-server"
                  ''' 
            }
        }
    }      
}
