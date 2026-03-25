pipeline {
    agent any

    tools {
        sonarRunner 'sonar-scanner'
    }

    environment {
        SONARQUBE = 'SonarQube'
    }

    stages {

        stage('Check Node') {
            steps {
                sh 'node -v'
                sh 'npm -v'
            }
        }

        stage('Install Backend') {
            steps {
                dir('backend') {
                    sh 'npm install'
                }
            }
        }

        stage('Install Frontend') {
            steps {
                dir('frontend') {
                    sh 'npm install'
                }
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh 'sonar-scanner'
                }
            }
        }

        stage('Build Frontend') {
            steps {
                dir('frontend') {
                    sh 'npm run build'
                }
            }
        }
    }
}
