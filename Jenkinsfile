#!groovy

pipeline {
    agent none

    options {
    timestamps()
    
  }


    stages {
        stage('Build') {
            agent any
                steps {
                    sh '''
                        echo test
                        env
                        echo $GIT_REF
                        '''
                }
        }
        
    }
}

// node ('master') {     
//     stage('Source') 
//     { // for display purposes      
//     // Get some code from our Git repository      
//     git 'https://github.com/brentlaster/gradle-greetings.git'      
// }
// }
