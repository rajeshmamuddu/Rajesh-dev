pipeline {
    agent any

    environment {
        // Define Docker registry credentials ID
        DOCKER_CREDENTIALS_ID = 'dockercred'
        // Define the name of your Docker image and tag
        DOCKER_IMAGE = 'docker.io/rajeshreactimage'
        DOCKER_TAG = 'latest'
    }

    stages {
        stage('Docker Login and Push') {
            steps {
                // Docker login
                withCredentials([usernamePassword(credentialsId: DOCKER_CREDENTIALS_ID, usernameVariable: 'dockercred', passwordVariable: 'dockercred')]) {
                    script {
                        def dockerLoginCmd = "docker login -u ${DOCKER_USERNAME} -p ${DOCKER_PASSWORD} ${DOCKER_IMAGE}"
                        sh dockerLoginCmd
                    }
                }

                // Build Docker image (replace this with your actual build steps)
                script {
                    def dockerBuildCmd = "docker build -t ${rajeshreactimage}:${latest} ."
                    sh dockerBuildCmd
                }

                // Push Docker image
                script {
                    def dockerPushCmd = "docker push ${rajeshreactimage}:${latest}"
                    sh dockerPushCmd
                }
            }
        }

        // Add more stages for your pipeline as needed
        stage('Additional Stages') {
            steps {
                // Your additional pipeline steps go here
            }
        }
    }
}
