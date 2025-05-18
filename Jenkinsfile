pipeline {
    agent any

    tools {
        maven 'Maven3'
        jdk 'JDK17'
        docker 'Docker'
    }

    environment {
        APP_NAME = 'shopping-cart'
        DOCKER_IMAGE = "mydockerhubuser/${APP_NAME}:latest"
    }

    stages {
        stage('Clone Code') {
            steps {
                echo 'Cloning repository...'
                git branch: 'main', url: 'https://github.com/AhmedSayed7/Ekart.git'
            }
        }

        stage('Build and Test') {
            steps {
                echo 'Building and running tests...'
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Archive JAR') {
            steps {
                echo 'Saving JAR file...'
                archiveArtifacts artifacts: 'target/*.jar'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t $DOCKER_IMAGE -f docker/Dockerfile .'
            }
        }
    }

    post {
        success {
            echo '✅ Build and Docker image created successfully.'
        }
        failure {
            echo '❌ Something went wrong during the pipeline.'
        }
    }
}
