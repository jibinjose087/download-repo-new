#!groovy​
pipeline {
    agent any
        stages {
            stage ('Input Parameter passing') {
                steps {
                 script {
                        // capture the approval details in approvalMap.
                        input id: 'SSAWS', message: 'Enter the Input Details', ok: 'Proceed?', parameters: [choice(choices: 'Dev\nStage\nProd', description: 'Choose the environemnt', name: 'ENV'), string(defaultValue: '', description: '', name: 'STACK_NAME'), string(defaultValue: '', description: '', name: 'APP'), choice(choices: 't2.micro', description: '', name: 'SSDevopsInstanceType')], submitter: 'Admin', submitterParameter: 'APPROVER'
                    } 
                      }
                }
            stage ('package stage') {
                steps {
                  echo "second stage"
                  }
                }
            stage ('archive stage') {
                steps {
                echo "deployed"                  
            }
          }
        }
  }
