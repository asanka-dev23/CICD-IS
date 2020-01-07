pipeline {
    agent any
    
    stages {
        stage('Git Pull') {
            steps {
                sh '''
                    cd /opt/ansible-scripts/
                    ansible-playbook -i staging git_pull.yaml --extra-vars "node=puppet-master"
                '''    
            }
        }
        stage('Applying Puupet to nodes') {
            steps {
                sh '''
                    cd /opt/ansible-scripts/
                    ansible-playbook -i staging puppet_apply.yaml --extra-vars "node=identity-server"
                ''' 
            }
        }
    }      
}
