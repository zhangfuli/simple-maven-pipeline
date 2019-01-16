pipeline {
    agent { docker 'maven:3.3.3' }
    stages {
        stage('Build') {
            steps{
                echo 'mvn version'
                sh 'mvn --version'
                sh 'mvn -B -DskipTests clean package'
                sh 'make'
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
        }
        stage('Test') {
            steps{
                sh 'make check || true'
                junit '**/target/*.xml'
            }

        }
        stage('Deploy') {
            when {
                expression {
                    currentBuild.result == null || currentBuild.result == 'SUCCESS'
                }
            }
            steps {
                sh 'make publish'
            }
        }
    }
}
