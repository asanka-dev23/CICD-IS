pipeline {
    agent any
    
    stages {
        stage('Puppet Apply') {
            environment{
                ENV = 'staging'
            }
            steps {
                echo 'Run Ansible Scripts'
                   //sh 'cd /opt/ansible-scripts/'
                   sh 'ansible-playbook -i staging /opt/ansible-scripts/puppet_apply.yaml --extra-vars "node=identity-server"' 
            }
        }
    }      
}
