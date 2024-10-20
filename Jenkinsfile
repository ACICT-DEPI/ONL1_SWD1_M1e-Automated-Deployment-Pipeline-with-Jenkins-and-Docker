pipeline {
    agent any

    stages {

        
        // stage('Build serverside docker') {
        //     steps {
        //       dir('ServerSide'){
        //         sh 'docker build -t serverside .'
        //       }
        //     }

        // }

        // stage('Build clientside docker') {
        //     steps {
        //       dir('ClientSide'){
        //         sh 'docker build -t clientside .'
        //       }
        //     }

        // }


        //  stage('Push Client Image to Docker Hub') {
        //     steps {
        //         script {
        //             // Use Docker Hub credentials (Username with Password)
        //             withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials', usernameVariable: 'DOCKERHUB_USER', passwordVariable: 'DOCKERHUB_PASS')]) {
        //                 sh 'echo $DOCKERHUB_PASS | docker login -u $DOCKERHUB_USER --password-stdin'
        //                 // Tag and push the clientside image
        //                 sh 'docker tag clientside $DOCKERHUB_USER/depi-project:client-latest'
        //                 sh 'docker push $DOCKERHUB_USER/depi-project:client-latest'
        //             }
        //         }
        //     }
        // }

        // stage('Push serverside Image to Docker Hub') {
        //     steps {
        //         script {
        //             // Use Docker Hub credentials (Username with Password)
        //             withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials', usernameVariable: 'DOCKERHUB_USER', passwordVariable: 'DOCKERHUB_PASS')]) {
        //                 sh 'echo $DOCKERHUB_PASS | docker login -u $DOCKERHUB_USER --password-stdin'
        //                 // Tag and push the serverside image
        //                 sh 'docker tag serverside $DOCKERHUB_USER/depi-project:server-latest'
        //                 sh 'docker push $DOCKERHUB_USER/depi-project:server-latest'
        //             }
        //         }
        //     }
        // }
        
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

    post {
        success {
            emailext(
                to: 'ialaamohamed321@gmail.com',
                subject: "Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' succeeded",
                body: "Good news! The job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' succeeded. Check the details at ${env.BUILD_URL}"
            )
        }
        failure {
            emailext(
                to: 'ialaamohamed321@gmail.com',
                subject: "Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' failed",
                body: "Unfortunately, the job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' failed. Check the details at ${env.BUILD_URL}"
            )
        }
    }
    
    
}


