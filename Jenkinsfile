pipeline {
    agent { docker 'maven:3.3.3' }
    stages {
        stage('Build Maven') {
            steps{
                echo 'mvn version'
                sh 'mvn --version'
                sh 'mvn package'
            }
        }
        stage('Build docker'){
            steps{
                sh 'docker build -t zhangfuli/pipeline_test:latest'
            }
            steps{
                echo 'run'
            }
        }

    }
}
