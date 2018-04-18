#!groovy
pipeline {
    agent any
        stages {
            stage ('Compile stage') {
                steps {
                    echo "compiled"                  
                }

            stage ('package stage') {
                steps {
                echo "packaged"                  
            }
            
            stage ('archive stage') {
                steps {
                echo "deployed"                  
            }
          }
        }
    }
