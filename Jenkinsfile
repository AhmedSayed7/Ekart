pipeline {
    agent any

    tools {
        maven 'Maven3'
        jdk 'JDK17'
    }

    stages {
        stage('Clone Code') {
            steps {
                echo 'Cloning the GitHub repository...'
                git branch: 'main', url: 'https://github.com/AhmedSayed7/Ekart.git'
            }
        }

        stage('Build Project') {
            steps {
                echo 'Building the project using Maven...'
                sh 'mvn clean package -Dmaven.test.failure.ignore=true'
            }
        }

        stage('Save JAR File') {
            steps {
                echo 'Saving the generated JAR file...'
                archiveArtifacts artifacts: 'target/*.jar'
            }
        }
    }

    post {
        success {
            echo '✅ Build completed successfully!'
        }
        failure {
            echo '❌ Build failed. Please check the logs.'
        }
    }
}
