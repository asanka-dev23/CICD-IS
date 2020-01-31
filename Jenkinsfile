pipeline {
    agent any
    
    stages {
        stage('Gitmerge') {
            steps {
                /*sh '''
                    cd /opt/ansible-scripts/
                    ansible-playbook -i staging git_pull.yaml --extra-vars "node=puppet-master"
                '''  */
                echo "Running : Git Merge"
            }
        }
        stage('Puppet Applying') {

            
        
            steps {
                catchError {
                /*sh '''
                    cd /opt/ansible-scripts/
                    ansible-playbook -i staging puppet_apply.yaml --extra-vars "node=identity-server"
                ''' */
                input message:'Do you want to proceed for Applying Puppet?'
                ech "Running : Applying Puppet"
                }
            }
            post {
                success {
                    echo 'Compile Stage Successful . . .'
                }
                failure {
                    /*echo 'Puppet Applying stage failed'*/
                    /*error('Puppet Applying stage failed')*/
                    input message:'Do you want to roll back?'
                    echo 'Rolling Back'
                }
            }
       
        }
        stage('Running Test Cases') {
            input {
                message "Do you want to run Test Cases ?"
            }   
            steps {
                /*sh '''
                    build '/Cloud_Tests/Staging/QA_Staging_Federation_SSO_For_AWS'
                 
                ''' */
                input message "Do you want to run QA_Staging_Federation_SSO_For_AWS ?"
                echo 'Running Test Cases'
            }
            steps {
                /*sh '''
                    build '/Cloud_Tests/Staging/QA_Staging_Federation_SSO_With_ADFS' 
                ''' */
                input message "Do you want to run QA_Staging_Federation_SSO_With_ADFS ?"
                echo 'Running Test Cases'
            }
            steps {
                /*sh '''
                    build '/Cloud_Tests/Staging/QA_Staging_Federation_SSO_With_Okta' 
                 
                ''' */
                input message "Do you want to run QA_Staging_Federation_SSO_With_Okta ?"
                echo 'Running Test Cases'
            }
        }
    }      
}
