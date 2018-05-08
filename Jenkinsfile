def approvalMap             // collect data from approval step

pipeline {
    agent any

    stages {
        stage('Stage 1') {
            steps {

            echso "First stage"
            }
        }
        stage('Stage 2') {

            steps {
                // print the details gathered from the approval
                echo "Hello second stage"
            }
        }
    }
    
    post {
      failure { 
            echo 'Mail send to approver'
        }
    }
}
