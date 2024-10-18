pipeline {
    agent any

    stages {

        
        stage('Build serverside docker') {
            steps {
              dir('ServerSide'){
                sh "docker build -t serverside'"
              }
            }

        }

        stage('Build clientside docker') {
            steps {
              dir('ClientSide'){
                sh "docker build -t clientside'"
              }
            }

        }


        stage('Push Client Image to Docker Hub') {
            steps {
                script {
                    // Log in to Docker Hub and push client image
                  //  sh "echo ${DOCKERHUB_CREDENTIALS_PSW} | docker login -u ${DOCKERHUB_CREDENTIALS_USR} --password-stdin"
                    sh 'docker tag serverside'
                    sh 'docker push alaamohamed09/depi-project:latest'
                }
            }
        }

         stage('Push serverside Image to Docker Hub') {
            steps {
                script {
                    // Log in to Docker Hub and push client image
                  //  sh "echo ${DOCKERHUB_CREDENTIALS_PSW} | docker login -u ${DOCKERHUB_CREDENTIALS_USR} --password-stdin"
                    sh 'docker tag clientside'
                    sh 'docker push alaamohamed09/depi-project:latest'
                }
            }
        }
        
     //   stage('Test') {
     //       steps {
                // Run Maven on a Unix agent.
             
      //          dir('ServerSide'){
      //          sh "dotnet test"
      //          }
              

      //      }

     //   }
        
         stage('Deploy') {
            steps {
            
                echo ' deplying... the application'

            }

        }
    }
    
    
}
