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
    }
}