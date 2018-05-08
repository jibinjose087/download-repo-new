def approvalMap             // collect data from approval step

pipeline {
    agent none

    stages {
        stage('Stage 1') {
            agent none
            steps {

                timeout(60) {                // timeout waiting for input after 60 minutes
                    script {
                        // capture the approval details in approvalMap.
                        approvalMap = input id: 'test', message: 'Hello', ok: 'Proceed?', parameters: [choice(choices: 'apple\npear\norange', description: 'Select a fruit for this build', name: 'FRUIT'), string(defaultValue: '', description: '', name: 'myparam')], submitter: 'user1,user2,group1', submitterParameter: 'APPROVER'
                    }
                }
            }
        }
        stage('Stage 2') {
            agent any

            steps {
                // print the details gathered from the approval
                echo "This build was approved by: ${approvalMap['APPROVER']}"
                echo "This build is brought to you today by the fruit: ${approvalMap['FRUIT']}"
                echo "This is myparam: ${approvalMap['myparam']}"
            }
        }
    }
}
