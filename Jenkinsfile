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
                echo 'Hello, JDK'
            }
        }
    }
}
