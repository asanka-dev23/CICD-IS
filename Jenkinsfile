pipeline {
    agent any
    
    stages {
        stage('Puppet Apply') {
            environment{
                ENV = 'staging'
            }
            steps {
                echo 'Run Ansible Scripts'
                   cd /opt/ansible-scripts/
                   sh 'ansible-playbook -i staging puppet_apply.yaml --extra-vars "node=identity-server"' 
            }
        }
    }      
}
