pipeline {
    agent any
    environment {
        DOCKER_REGISTRY_HOST = "registry.dop.clsaa.com"
        DOCKER_REGISTRY = "registry.dop.clsaa.com/1171067930/simple-maven-test"
        BUILD_TAG = "latest"
    }
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
                sh 'docker build -t ${DOCKER_REGISTRY}:${BUILD_TAG} ./'
            }
        }
        stage('Push Docker'){
            steps{
                echo 'push'
               
                withCredentials([usernamePassword(credentialsId: 'docker_registry', passwordVariable: 'password', usernameVariable: 'username')]) {
<<<<<<< HEAD
                    echo "${username}"
                    echo "${password}"
=======
>>>>>>> checkout-test
                      sh "docker login -u ${username} -p ${password} ${DOCKER_REGISTRY_HOST}"
                      sh "docker push ${DOCKER_REGISTRY}:${BUILD_TAG}"
                  }
             }
        }
        stage('Deploy'){
            steps{
                echo 'deploy'
                sh "docker run -itd -p 8081:8081 ${DOCKER_REGISTRY}:${BUILD_TAG}"
             }
        }
    }
}
