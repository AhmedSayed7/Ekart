pipeline {
    agent any

    tools {
        maven "Maven3"
        jdk "JDK17"
    }

    stages {
        stage('Build') {
            steps {

                git branch: 'main', url: 'https://github.com/AhmedSayed7/Ekart.git'


                sh "mvn -Dmaven.test.failure.ignore=true clean package"

                
            }

            post {

                success {
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
}
