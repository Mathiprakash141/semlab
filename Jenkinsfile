pipeline {
    agent any

    // trigger by GitHub webhook
    triggers {
        githubPush()
    }

    environment {
        // Example env vars — customise as needed
        REPO_URL = 'https://github.com/Mathiprakash141/semlab.git'
        BRANCH = 'main'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: "${env.BRANCH}"]],
                    userRemoteConfigs: [[url: "${env.REPO_URL}"]]
                ])
            }
        }

        stage('Build') {
            steps {
                // Replace the following with your build command
                echo "Building project..."
                // e.g. sh 'mvn clean package' or sh 'npm install' etc.
            }
        }

        stage('Test') {
            steps {
                // Replace with your test command
                echo "Running tests..."
                // e.g. sh 'mvn test' or sh 'npm test'
            }
        }

        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                // Replace with your deploy steps
                echo "Deploying to environment..."
            }
        }
    }

    post {
        success {
            echo "Pipeline succeeded!"
        }
        failure {
            echo "Pipeline failed!"
        }
    }
}
