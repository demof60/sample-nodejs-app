pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {
        stage('Clone') {
            steps {
                git url: 'https://github.com/demof60/sample-nodejs-app.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'npm test'
            }
        }

        stage('Build Complete') {
            steps {
                echo 'Build and test stages completed successfully.'
            }
        }
    }
}
