pipeline {
    agent { docker 'maven:3.3.3' }
    stages {
        stage('Build Maven') {
            steps{
                echo 'mvn version'
                sh 'mvn --version'
                sh 'mvn clean package -Dmaven.test.skip=true'
                sh 'mvn package'
            }
        }
        stage('Build Docker'){
            steps{
                echo 'run'
                sh 'docker build -t zhangfuli/pipeline_test:latest ./'
            }
        }
    }
}
