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
            steps{
                git branch: 'main',
                url: 'https://github.com/Manjeetmathur/testing-jenkins'
            }
        }   
        stage("docker image building"){
            steps{
                sh 'docker build -t ${IMAGE_NAME} .'
            }
        }

        stage("stop and remove previous container"){
            steps{
                sh ''' 
                    docker stop ${CONTAINER_NAME} || true
                    docker rm ${CONTAINER_NAME} || true
                '''
            }
        }

        stage("run container"){
            steps{
                sh ''' 
                    docker run -d -p ${PORT}:${PORT} --name ${CONTAINER_NAME} ${IMAGE_NAME}:latest
                '''
            }
        }


    }
}