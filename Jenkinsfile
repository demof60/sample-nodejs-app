pipeline {
    agent any

    triggers {
        githubPush() // Trigger build on push to GitHub
    }

    tools {
        nodejs 'NodeJS 18' // Ensure Node.js is configured in Jenkins Global Tools
    }

    stages {
        stage('Clone') {
            steps {
                git url: 'https://github.com/demof60/sample-nodejs-app.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }

        stage('Build Complete') {
            steps {
                echo 'Build and test stages completed successfully.'
            }
        }
    }
}
