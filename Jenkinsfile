pipeline {
    agent any 
    options {
    skipDefaultCheckout true
  }
    stages {
        stage('First stage') {
            steps {
                echo 'Hello, Maven'
            }
        }
        stage('Second stage') {
            steps {
                eho 'Hello, JDK'
            }
        }
    }
    
        post { 
        success { 
            echo 'Current build is success'
        }
        changed { 
            echo 'Previous one is success but this one failed'
        }
    }
    
}
