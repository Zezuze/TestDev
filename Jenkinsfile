pipeline {
    agent any

    environment {
        GIT_URL = 'git@github.com:Zezuze/TestDev.git'
        GIT_BRANCH = 'main'
        BUILD_NAME = 'app'
        PROJECT_URL = 'http://localhost:8081'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: "${GIT_BRANCH}", url: "${GIT_URL}"
            }
        }

        stage('Build Docker image') {
            steps {
                sh "docker build -t ${BUILD_NAME} ."
            }
        }

        stage('Run Container') {
            steps {
                sh """
                docker ps -q --filter "name=${BUILD_NAME}" | grep -q . && docker rm -f ${BUILD_NAME} || true
                docker run -d --name ${BUILD_NAME} -p 8081:80 ${BUILD_NAME}
                """
            }
        }

        stage('Test Deployment') {
            steps {
                sh "curl -I ${PROJECT_URL} || exit 1"
            }
        }
    }

    post {
        success {
            echo '✅ Deployment successful!'
        }
        failure {
            echo '❌ Deployment failed!'
        }
    }
}
