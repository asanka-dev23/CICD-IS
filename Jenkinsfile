pipeline {
    agent any
    
    stages {
        stage('Run Ansible') {
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
