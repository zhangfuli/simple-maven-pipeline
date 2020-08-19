pipeline {
    agent any
    environment {
        DOCKER_REGISTRY_HOST = "registry.dop.clsaa.com"
        DOCKER_REGISTRY = "registry.dop.clsaa.com/dop/dop-web"
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
                sh 'docker login -u username -p password'
                withCredentials([usernamePassword(credentialsId: 'docker_registry', passwordVariable: 'password', usernameVariable: 'username')]) {
                      sh "docker login -u ${username} -p ${password} ${DOCKER_REGISTRY_HOST}"
                      sh "docker push ${DOCKER_REGISTRY}:${build_tag}"
                  }
                sh 'docker push ${DOCKER_REGISTRY}:${BUILD_TAG}'
             }
        }
    }
}
