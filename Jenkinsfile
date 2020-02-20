pipeline {
    agent any
    
    stages {
        stage('Create Stack') {
            steps {
                 sh '''
                        build '/CreateStack-ISCICD'
                    ''' 
                /*sh '''
                    cd /opt/ansible-scripts/
                    ansible-playbook -i staging git_pull.yaml --extra-vars "node=puppet-master"
                '''  */
                echo $cicdis_PrivateIp1
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
                echo "Running : Applying Puppet"
                }
            }
            post {
                success {
                    echo 'Compile Stage Successful . . .'
                    input message: "Do you want to run QA_Staging_Federation_SSO_For_AWS ?"

                    echo 'Running Test Case QA_Staging_Federation_SSO_For_AWS '
                    /*sh '''
                        build '/Cloud_Tests/Staging/QA_Staging_Federation_SSO_For_AWS'
                    ''' */
                    input message: "Do you want to run QA_Staging_Federation_SSO_With_ADFS ?"
                    echo 'Running Test Case QA_Staging_Federation_SSO_With_ADFS'
                    /*sh '''
                        build '/Cloud_Tests/Staging/QA_Staging_Federation_SSO_With_ADFS' 
                    ''' */
                    input message: "Do you want to run QA_Staging_Federation_SSO_With_Okta ?"
                    echo 'Running Test Case QA_Staging_Federation_SSO_With_Okta'
                    /*sh '''
                        build '/Cloud_Tests/Staging/QA_Staging_Federation_SSO_With_Okta' 
                    ''' */
                }
                failure {
                    /*echo 'Puppet Applying stage failed'*/
                    /*error('Puppet Applying stage failed')*/
                    input message:'Do you want to roll back?'
                    echo 'Rolling Back'
                }
            }
       
        }

    }      
}
