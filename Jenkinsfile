    pipeline {
    agent any
    environment {
        CI = 'true'
        API = './coffeeAPI'
    }
    stages {
        stage('Deploy to Dev') {
            environment{
                ENV = 'dev'
            }
            steps {
                echo 'Deploying to Dev'
                withCredentials([usernamePassword(credentialsId: 'apim', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                   sh 'apimcli login $ENV -u $USERNAME -p $PASSWORD -k'
                   sh 'apimcli import-api -f $API -e $ENV -k --preserve-provider=false --update --verbose'
                }
            }
        }
        stage('Deploy to Staging') {
            environment{
                ENV = 'stage'
            }
            steps {
                echo 'Deploying to Staging'
                withCredentials([usernamePassword(credentialsId: 'apim', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                   sh 'apimcli login $ENV -u $USERNAME -p $PASSWORD -k'
                   sh 'apimcli import-api -f $API -e $ENV -k --preserve-provider=false --update --verbose'
                }
            }
        }
    }
}
