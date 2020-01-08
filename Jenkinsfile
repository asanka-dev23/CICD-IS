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
       /* stage('Applying Puppet to nodes') {
            steps {
                sh '''
                    cd /opt/ansible-scripts/
                    ansible-playbook -i staging puppet_apply.yaml --extra-vars "node=identity-server"
                ''' 
            }
        }
        stage('Running Test Cases') {
            steps {
                //sh '''
                    build '/Cloud_Tests/Staging/QA_Staging_Federation_SSO_For_AWS'
                    build '/Cloud_Tests/Staging/QA_Staging_Federation_SSO_With_ADFS'
                    build '/Cloud_Tests/Staging/QA_Staging_Federation_SSO_With_Okta'
                //''' 
            }
        }*/
    }      
}
