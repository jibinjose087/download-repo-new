pipeline {
    agent any 
    options {
    skipDefaultCheckout true
  }
    stages {
        stage('First stage') {
            steps {
                 timeout(60) {                // timeout waiting for input after 60 minutes
                    script {
                        // capture the approval details in approvalMap.
                        approvalMap = input id: 'test', message: 'Hello', ok: 'Proceed?', parameters: [choice(choices: 'apple\npear\norange', description: 'Select a fruit for this build', name: 'FRUIT'), string(defaultValue: '', description: '', name: 'myparam')], submitter: 'user1,user2,group1', submitterParameter: 'APPROVER'
                    }
                }
            }
            }
        }
        stage('Second stage') {
            steps {
                eho 'Hello, JDK'
            }
        }
    }
    
        post { 
        changed { 
            echo 'Current build is success'
        }
        failure { 
            echo 'Previous one is success but this one failed'
        }
    }
    
}
