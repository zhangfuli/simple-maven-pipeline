pipeline {
    agent { docker 'maven:3.3.3' }
    stages {
        stage('Build') {
            steps{
                echo 'mvn version'
                sh 'mvn --version'
                sh 'mvn -B -DskipTests clean package'
            }
           
        }
    }
}
