pipeline {
    agent any

    environment {
        GIT_BRANCH = "main"
	GIT_CREDENTIAL = "jenkins-ssh"
	GIT_URL = "git@github.com:Zezuze/TestDev.git/"
    }
       
    stages {
        stage('Checkout') {
            steps {
                git branch: "$GIT_BRANCH",
		    url: "$GIT_URL",
		    credentialsId: "$GIT_CREDENTIAL"
            }
        }
    }

    post {
        success { echo "SUCCESS" }
        failure { echo "FAILED" }
    }
}

