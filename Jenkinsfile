pipeline {
    agent any
    
    stages {
        stage('Puppet Apply') {
            environment{
                ENV = 'staging'
            }
            steps {
                echo 'Run Ansible Scripts'
                   sh 'cd /opt/ansible-scripts/'
                   sh 'ansible-playbook -i staging git_pull.yaml --extra-vars "node=puppet-master"' 
            }
        }
    }      
}
