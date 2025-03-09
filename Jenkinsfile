pipeline{
    agent {label 'ubuntu-agent'}
    stages{
        stage('CodeScan'){
            steps{
                sh 'touch file.txt'
                sh 'echo "It works! ">file.txt'
                sh 'cat file.txt'
            }
        }

        stage('TestingUbuntu'){
            steps{
                sh "python3 --version"
                sh "docker --version"
                sh "java --version"
            }
        }
    }
}