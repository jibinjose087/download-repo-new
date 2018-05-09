#!groovy​
pipeline {
    agent any
        stages {
            stage ('Input Parameter passing') {
                steps {
                    echo "$ENV, $APP" 
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
