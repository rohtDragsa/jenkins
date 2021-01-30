#!groovy

pipeline {
    agent any

    stages {
        stage("Checkout") {
            steps {
            
                sh """
                whoami
                git clone git@github.com:rohtDragsa/jenkins.git
                """
            }
        }
    }
}



//pipeline-terrform
//https://www.nbcnews.com/think/opinion/redditors-took-hedge-funds-over-gamestop-amc-theatres-stock-won-ncna1255919


// node ('master') {     
//     stage('Source') 
//     { // for display purposes      
//     // Get some code from our Git repository      
//     git 'https://github.com/brentlaster/gradle-greetings.git'      
// }
// }
