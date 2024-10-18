pipeline {
    agent any

    stages {
        
        stage('Build') {
            steps {
               
             //   echo ' building the application'
                    sh 'docker compuse up'
            }

        }
        
        stage('Test') {
            steps {
                // Run Maven on a Unix agent.
               // sh "cd ServerSide/Api.Tests"
               // sh "dotnet test"
                echo ' testing the application'

            }

        }
        
         stage('Deploy') {
            steps {
            
                echo ' deplying the application'

            }

        }
    }
    
    
}
