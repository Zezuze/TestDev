pipeline {
    agent any

    environment {
        GIT_URL = "git@github.com:Zezuze/TestDev.git"
        GIT_BRANCH = "main"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: "$GIT_BRANCH",
		    credentialsId: "jenkins-ssh",
		    url: "$GIT_URL"
            }
        }
    }

    post {
        success { echo "SUCCESS" }
        failure { echo "FAILED" }
    }
}
