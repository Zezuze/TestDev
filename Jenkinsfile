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
                git branch: "${GIT_BRANCH}", credentialsId: "jenkins-ssh", url: "${GIT_URL}"
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
