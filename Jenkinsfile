pipeline {
    agent any

    stages {
        stage('build'){
            steps{
            sh 'mvn clean package'    
            sh 'java -jar target/spring-boot-web.jar'
            }
        }

        stage('deploy'){
            steps{
                sh 'docker build -t spring-boot-t3'
                
            }
        }
    }
}