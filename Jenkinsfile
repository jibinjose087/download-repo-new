def approvalMap             // collect data from approval step

pipeline {
    agent any

    stages {
        stage('Stage 1') {
            steps {

                 script {
                        // capture the approval details in approvalMap.
approvalMap = input id: 'AWS', message: 'Enter the respective fields', ok: 'Proceed?', parameters: [choice(choices: ['Dev', 'Stage', 'Prod'], description: 'Environments', name: 'EnvType'), string(defaultValue: 'AppName', description: '', name: 'InstanceType')], submitter: '"admin, bob"', submitterParameter: 'APPROVER'

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
