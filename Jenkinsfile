pipeline {
    agent any
    
    stages {
        stage('Gitmerge_IS_Cloud') {
            steps {
                /*sh '''
                    cd /opt/ansible-scripts/
                    ansible-playbook -i staging git_pull.yaml --extra-vars "node=puppet-master"
                '''  */
                echo "Running : Git Merge"
            }
        }
        stage('Applying Puppet to nodes') {
            input{
                message "Do you want to proceed for Applying Puppet?"
            }
            steps {
                catchError {
                /*sh '''
                    cd /opt/ansible-scripts/
                    ansible-playbook -i staging puppet_apply.yaml --extra-vars "node=identity-server"
                ''' */
                ech "Running : Applying Puppet"
                }
            }
            post {
                success {
                    echo 'Compile Stage Successful . . .'
                }
                failure {
                    /*echo 'Puppet Applying stage failed'*/
                    error('Puppet Applying stage failed')
                    echo 'Rolling Back'
                }
            }
       
        }
        stage('Running Test Cases') {
            input{
                message "Do you want to run Test Cases"
            }
            steps {
                /*sh '''
                    build '/Cloud_Tests/Staging/QA_Staging_Federation_SSO_For_AWS'
                    build '/Cloud_Tests/Staging/QA_Staging_Federation_SSO_With_ADFS'
                    build '/Cloud_Tests/Staging/QA_Staging_Federation_SSO_With_Okta' 
                 
                ''' */
                echo 'Running Test Cases'
            }
        }
    }      
}
