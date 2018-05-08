#!groovy​
pipeline {
    agent any
        tools { 

            }
        stages {
            stage ('Compile stage') {
                steps {
                sh  echo "first stage"
                      }
                }
            stage ('package stage') {
                steps {
                  sh  echo "second stage"
                  }
                }
            stage ('archive stage') {
                steps {
                sh echo "deployed"                  
            }
            }
            post {
                success {
                      echo "success"                  
                always { 
                    cleanWs()
                }
            }
          }
        }
    }
  }
