pipeline {
    agent any
    
    stages {
        stage('Puppet Apply') {
            environment{
                ENV = 'staging'
            }
            steps {
                sh '''
                    echo 'Run Ansible Scripts'
                    cd /opt/ansible-scripts/
                    ansible-playbook -i staging git_pull.yaml --extra-vars "node=puppet-master"
                    echo 'Run Ansible Scripts'
                    cd /opt/ansible-scripts/
                    ansible-playbook -i staging puppet_apply.yaml --extra-vars "node=identity-server"
                '''    
                build job: 'QA_Staging_Federation_SSO_For_AWS'
            }
        }
    }      
}
