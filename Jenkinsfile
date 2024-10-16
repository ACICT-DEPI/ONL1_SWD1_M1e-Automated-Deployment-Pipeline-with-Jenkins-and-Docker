pipeline {
    agent any

    stages {
        
        //  stage('Checkout') {
        //     steps {
        //     // Get some code from a GitHub repository
        //         git 'https://github.com/AlaaMohamed09/DEPI-Graduationproject.git'
        //         sh "ls"
        // }

        // }
        
        
        stage('Build') {
            steps {
               
                echo ' building the application'
            
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
