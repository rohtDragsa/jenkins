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


//pipeline-terrform
https://www.nbcnews.com/think/opinion/redditors-took-hedge-funds-over-gamestop-amc-theatres-stock-won-ncna1255919


// node ('master') {     
//     stage('Source') 
//     { // for display purposes      
//     // Get some code from our Git repository      
//     git 'https://github.com/brentlaster/gradle-greetings.git'      
// }
// }
