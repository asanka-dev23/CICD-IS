pipeline {
    agent any
    
    stages {
        stage('Git Pull') {
            environment{
                ENV = 'staging'
            }
            steps {
                echo 'Run Ansible Scripts'
                   sh 'cd /opt/ansible-scripts/'
                   sh 'ansible-playbook -i staging git_pull.yaml --extra-vars "node=puppet-master"' 
            }
        }
        stage('Puppet Apply') {
            environment{
                ENV = 'staging'
            }
            steps {
                echo 'Run Ansible Scripts'
                   sh 'cd /opt/ansible-scripts/'
                   sh 'ansible-playbook -i staging puppet_apply.yaml --extra-vars "node=identity-server"' 
            }
        }
    }      
}
