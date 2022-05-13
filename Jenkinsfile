pipeline {
    agent any

    stages {
        stage('Tagging the build') {
            steps {
                sh 'git tag build-$BUILD_NUMBER'
                withCredentials([gitUsernamePassword(credentialsId: 'jenkins-task3', gitToolName: 'git-tool')]) {
            sh "git push --tags"
          }
            }
        }
        stage('build'){
            steps{
            sh 'mvn clean package'
            }
        }

        stage('deploy'){
            steps{
                sh 'docker build -t keerthi-jenkins-task3 .'   
            }
        }

        stage('push ECR'){
            steps{
                withDockerRegistry( [ credentialsId: "ecr:us-east-1:aws-credentials", url: "https://590852515231.dkr.ecr.us-east-1.amazonaws.com" ] ){
                    sh 'docker tag keerthi-jenkins-task3:latest 590852515231.dkr.ecr.us-east-1.amazonaws.com/keerthi-jenkins-task3:$BUILD_NUMBER'
                    sh 'docker push 590852515231.dkr.ecr.us-east-1.amazonaws.com/keerthi-jenkins-task3:$BUILD_NUMBER'
                }  

            }
        }
    }
}
