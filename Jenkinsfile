pipeline {
    agent any

    stages {
        stage('Build serverside docker') {
            steps {
                dir('ServerSide') {
                    sh 'docker build -t serverside .'
                }
            }
        }

        stage('Build clientside docker') {
            steps {
                dir('ClientSide') {
                    sh 'docker build -t clientside .'
                }
            }
        }

        stage('Push Client Image to Docker Hub') {
            steps {
                script {
                    // Use Docker Hub credentials (Username with Password)
                    withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials', usernameVariable: 'DOCKERHUB_USER', passwordVariable: 'DOCKERHUB_PASS')]) {
                        sh 'echo $DOCKERHUB_PASS | docker login -u $DOCKERHUB_USER --password-stdin'
                        // Tag and push the clientside image
                        sh 'docker tag clientside $DOCKERHUB_USER/depi-project:client-latest'
                        sh 'docker push $DOCKERHUB_USER/depi-project:client-latest'
                    }
                }
            }
        }

        stage('Push serverside Image to Docker Hub') {
            steps {
                script {
                    // Use Docker Hub credentials (Username with Password)
                    withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials', usernameVariable: 'DOCKERHUB_USER', passwordVariable: 'DOCKERHUB_PASS')]) {
                        sh 'echo $DOCKERHUB_PASS | docker login -u $DOCKERHUB_USER --password-stdin'
                        // Tag and push the serverside image
                        sh 'docker tag serverside $DOCKERHUB_USER/depi-project:server-latest'
                        sh 'docker push $DOCKERHUB_USER/depi-project:server-latest'
                    }
                }
            }
        }

        stage('Test') {
            steps {
                dir('ServerSide') {
                    // Run tests
                    sh "dotnet test"
                }
            }
        }

        stage('Deploy to EC2') {
            steps {
                script {
                    // Use SSH credentials stored in Jenkins to SSH into EC2 and deploy the app
                    sshagent(['ec2-ssh-credentials']) {
                        sh '''
                            ssh -o StrictHostKeyChecking=no root@ec2-34-249-200-147.eu-west-1.compute.amazonaws.com << EOF
                                # Navigate to the home directory
                                cd /home

                                # Start services defined in docker-compose.yml
                                docker-compose up -d || { echo "Docker-compose failed"; exit 1; }

                                echo "Deployment complete"
                            EOF
                        '''
                    }
                }
            }
        }
    }

    post {
        success {
            emailext(
                to: 'ialaamohamed123@gmail.com',
                subject: "Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' succeeded",
                body: "Good news! The job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' succeeded. Check the details at ${env.BUILD_URL}"
            )
        }
        failure {
            emailext(
                to: 'ialaamohamed123@gmail.com',
                subject: "Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' failed",
                body: "Unfortunately, the job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' failed. Check the details at ${env.BUILD_URL}"
            )
        }
    }
}
