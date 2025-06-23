pipeline {
    agent any

    environment {
        SONARQUBE_ENV = 'MySonarQubeServer' // Name of SonarQube instance in Jenkins settings
    }

    triggers {
        githubPush() // Trigger build on push to GitHub
    }

    tools {
        nodejs 'NodeJS 18' // Ensure Node.js tool is defined in Jenkins → Global Tool Configuration
    }

    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/your-user/your-repo.git', branch: 'main'
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

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv("${SONARQUBE_ENV}") {
                    sh 'npx sonar-scanner'
                }
            }
        }

        stage('Quality Gate') {
            steps {
                timeout(time: 1, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }

        stage('Build Complete') {
            steps {
                echo 'Build and Analysis completed successfully.'
            }
        }
    }
}
