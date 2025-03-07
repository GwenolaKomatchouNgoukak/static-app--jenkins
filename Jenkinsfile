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
        stage('build'){
            steps{
                sh 'docker build -t webapp .'
                sh 'docker images'
            }
        }
    }
}