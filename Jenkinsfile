#!groovy​
pipeline {
    agent any
        stages {
            stage ('Input Parameter passing') {
                steps {
                 script {
                input id: 'Cloudformation', message: 'Enter the Input Details', ok: 'Are you sure?', parameters: [choice(choices: ['Dev', 'Stage', 'Prod'], description: '', name: 'ENV'), string(defaultValue: '', description: '', name: 'STACK_NAME', trim: false), string(defaultValue: '', description: '', name: 'APP', trim: false), choice(choices: ['t2.micro'], description: '', name: 'SSDevopsInstanceType')], submitter: 'Admin', submitterParameter: 'Admin'
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
