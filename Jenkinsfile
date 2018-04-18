#!groovy​
pipeline {
    agent any
        tools { 
        maven 'Maven 3.5.3' 
            }
        stages {
            stage ('Compile stage') {
                steps {
                sh  '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                    echo "compiled"                  
                    '''
                      }
                }
            stage ('package stage') {
                steps {
                echo "packaged"                  
                    }
                }
            stage ('archive stage') {
                steps {
                echo "deployed"                  
            }
            post {
                success {
                    echo "Successfull" 
            }
          }
        }
    }
