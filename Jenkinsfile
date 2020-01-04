    pipeline {
    agent any
    //environment {
        //CI = 'true'
        //API = './coffeeAPI'
    //}
    stages {
        stage('Run Ansible') {
            environment{
                ENV = 'staging'
            }
            steps {
                echo 'Run Ansible Scripts'
                //withCredentials([usernamePassword(credentialsId: 'apim', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                   sh 'cd /opt/ansible-scripts/'
                   sh 'ansible-playbook -i staging puppet_apply.yaml --extra-vars "node=identity-server"'             
                  // sh 'apimcli import-api -f $API -e $ENV -k --preserve-provider=false --update --verbose'
                }
            }
        }
        stage('Testing') {
            environment{
                ENV = 'stage'
            }
            steps {
                echo 'Successfully Run Ansible'
                //withCredentials([usernamePassword(credentialsId: 'apim', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                   //sh 'apimcli login $ENV -u $USERNAME -p $PASSWORD -k'
                   //sh 'apimcli import-api -f $API -e $ENV -k --preserve-provider=false --update --verbose'
                }
            }
        }
    }
}
