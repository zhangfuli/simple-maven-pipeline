pipeline {
    agent { docker 'maven:3.3.3' }
    stages {
        stage('Build_Maven') {
            steps{
                echo 'mvn version'
                sh 'mvn --version'
                sh 'mvn package'
            }
        }
        stage('Build_Docker'){
            steps{
                sh 'docker build -t zhangfuli/pipeline_test:latest'
            }
            steps{
                echo 'run'
            }
        }

    }
}
