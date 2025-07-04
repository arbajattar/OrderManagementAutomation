// Dummy content for Jenkinsfilepipeline {
    agent any

    environment {
        MAVEN_OPTS = '-Dmaven.repo.local=.m2/repository'
    }

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/arbajattar/OMS_HybridAutomation.git'
            }
        }

        stage('Build & Test with Docker') {
            steps {
                sh 'docker-compose up --build --abort-on-container-exit'
            }
        }

        stage('Report') {
            steps {
                junit 'target/surefire-reports/*.xml'
            }
        }
    }

    post {
        always {
            sh 'docker-compose down'
        }
    }
}
