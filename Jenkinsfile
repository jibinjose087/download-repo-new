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
        changed { 
            echo 'Current build is success'
        }
        failure { 
            echo 'Previous one is success but this one failed'
        }
    }
    
}
