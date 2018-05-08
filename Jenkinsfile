def approvalMap             // collect data from approval step

pipeline {
    agent any

    stages {
        stage('Stage 1') {
            steps {

            echo "First stage"
            }
        }
        stage('Stage 2') {

            steps {
                // print the details gathered from the approval
                #echo "This build was approved by: ${approvalMap['APPROVER']}"
                #echo "This build is brought to you today by the fruit: ${approvalMap['FRUIT']}"
                #echo "This is myparam: ${approvalMap['myparam']}"
                echo "Hello second stage"
            }
        }
    }
}
