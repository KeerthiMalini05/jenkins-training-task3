pipeline {
    agent any

    stages {
        stage('build'){
            steps{
            sh 'mvn clean package'
            }
        }

        stage('deploy'){
            steps{
                sh 'docker build -t spring-boot-t3 .'   
            }
        }
    }
}