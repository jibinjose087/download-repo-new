def approvalMap             // collect data from approval step

pipeline {
    agent any

    stages {
        stage('Stage 1') {
            steps {

            timeout(60) {                // timeout waiting for input after 60 minutes
                 script {
                        // capture the approval details in approvalMap.
                     input message: 'Enter the respective fields', ok: 'Proceed?', parameters: [choice(choices: ['Dev', 'Stage', 'Prod'], description: 'Environments', name: 'EnvType'), string(defaultValue: 'AppName', description: '', name: 'InstanceType', trim: false)], submitter: '"admin, bob"'
                    }
                }
            
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
      always { 
            cleanWs()
        }
    }
}
