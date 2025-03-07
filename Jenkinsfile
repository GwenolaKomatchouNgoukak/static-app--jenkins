pipeline{
    agent any
    stages{
        stage('CodeScan'){
            steps{
                sh 'touch file.txt'
                sh 'echo "It works! ">file.txt'
                sh 'cat file.txt'
                sh 'trivy fs . -o file.txt'
                sh 'cat file.txt'
            }
        }
        stage('DockerLogin'){
            steps{
                sh 'aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 767397795869.dkr.ecr.us-east-1.amazonaws.com'
            }
        }
        stage('build'){
            steps{
                sh 'docker build -t dev-studygroup .'
                sh 'docker build -t newversion .'

                sh 'docker tag dev-studygroup:latest 767397795869.dkr.ecr.us-east-1.amazonaws.com/dev-studygroup:latest'
                sh 'docker tag dev-studygroup:latest 767397795869.dkr.ecr.us-east-1.amazonaws.com/dev-studygroup:v1.$BUILD_NUMBER'

                sh 'docker push 767397795869.dkr.ecr.us-east-1.amazonaws.com/dev-studygroup:latest'
                sh 'docker push 767397795869.dkr.ecr.us-east-1.amazonaws.com/dev-studygroup:v1.$BUILD_NUMBER'
            }
        }
        stage('Testing'){
            steps{
                sh 'docker images'
                sh 'docker run -itd --name web -p 80:81 webapp'
                sh 'docker ps'
            }
        }
    }
}