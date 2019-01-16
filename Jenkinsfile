pipeline {
    agent { docker 'maven:3.3.3' }
    stages {
        stage('Build') {
            steps{
                echo 'mvn version'
                sh 'mvn --version'
                sh 'docker build -f zhangfuli/pipeline_test:latest'
            }
        }
        stage('Run'){
            steps{
                echo 'run'

            }
        }

    }
}
