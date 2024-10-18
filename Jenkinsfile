pipeline {
    agent any

    stages {


        stage('Install Docker Compose') {
            steps {
                sh '''
                if ! [ -x "$(command -v docker-compose)" ]; then
                  sudo curl -L "https://github.com/docker/compose/releases/download/v2.21.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
                  sudo chmod +x /usr/local/bin/docker-compose
                fi
                '''
            }
        }
        
        stage('Build') {
            steps {
                sh 'docker-compose up'
            }

        }
        
        stage('Test') {
            steps {
                // Run Maven on a Unix agent.
               // sh "cd ServerSide/Api.Tests"
               // sh "dotnet test"
                echo ' testing.. the application'

            }

        }
        
         stage('Deploy') {
            steps {
            
                echo ' deplying... the application'

            }

        }
    }
    
    
}
