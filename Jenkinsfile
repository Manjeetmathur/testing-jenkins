pipeline {
    agent any 

    environment {
        CONTAINER_NAME = "nestjs-app"
        IMAGE_NAME = "nestjs-image"
        EMAIL = "manjeetkumar62054@gmail.com"
        PORT = "3000"
    }

    stages {
        stage('Clone Repo') {
            echo "Cloing is in process..."

            steps{
                git branch: 'main',
                url: 'https://github.com/Manjeetmathur/testing-jenkins'
            }
        }   
        stage("docker image building"){
            echo "docker image is getting build"

            steps{
                sh 'docker build -t ${IMAGE_NAME}'
            }
        }

        stage("stop and remove previous container"){
            echo "stoping and removing previous container"

            steps{
                sh ''' 
                    docker stop ${CONTAINER_NAME} || true
                    docker rm ${CONTAINER_NAME} || true
                '''
            }
        }

        stage("run container"){
            echo "container is getting started"

            steps{
                sh ''' 
                    docker run -d -p ${PORT}:${PORT} --name ${CONTAINER_NAME} ${IMAGE_NAME}:latest
                '''
            }
        }

        stage("send email notification"){
            echo "email is getting send"

            steps {
                emailtext(
                    subject: "Nest js app deployed successfully"
                    body: "Your nest js app deployed"
                    to: "${EMAIL}"
                )
            }
        }

    }
}