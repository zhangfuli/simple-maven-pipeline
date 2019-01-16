pipeline {
    agent any
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
