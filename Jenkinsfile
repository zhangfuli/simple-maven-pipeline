pipeline {
    agent { docker 'maven:3.3.3' }
    stages {
        stage('Build') {
            steps{
                echo 'mvn version'
                sh 'mvn --version'
           
                sh 'docker build'
                sh 'docker tag dop-test:latest'
            }
        }

    }
}
