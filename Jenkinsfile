pipeline {
    agent any
    
    stages {
        stage('Git Pull') {
            steps {
                sh '''
                    echo 'Git Pull from Puppet-IS-Cloud puppet5-staging branch'
                    cd /opt/ansible-scripts/
                    ansible-playbook -i staging git_pull.yaml --extra-vars "node=puppet-master"
                '''    
            }
        }
        stage('Puppet Apllying with ') {
            steps {
                sh '''
                    echo 'Run Ansible Scripts'
                    cd /opt/ansible-scripts/
                    ansible-playbook -i staging puppet_apply.yaml --extra-vars "node=identity-server"
                ''' 
            }
        }
    }      
}
