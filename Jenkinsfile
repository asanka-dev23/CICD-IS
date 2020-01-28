pipeline {

agent any
stages{
    stage('Build-Initiator-Info'){
            steps{
                sh 'echo "Send Info"'
            }
    }
    stage('Build') {
     input{
    message "Do you want to proceed for Dep?"
   }    
        steps{
             catchError {
                sh 'echo "This is build"'
            }
         }
         post {
            success {
                echo 'Compile Stage Successful . . .'
            }
            failure {
                echo 'Compile stage failed'
                error('Stopping early…')

             }
    }
   }
  stage ('Deploy To Prod'){
  input{
    message "Do you want to proceed for production deployment?"
  }
    steps {
                sh 'echo "Deploy into Prod"'

              }
        }
  }
}
