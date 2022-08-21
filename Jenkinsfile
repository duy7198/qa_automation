pipeline {
    agent any

    stages {
        stage('Verify branch') {
            steps {
                echo "${GIT_BRANCH}"
            }
        }
        stage('Docker buidling') {
            steps {
                bat 'docker images -a'
                bat 'cd azure-vote && docker build -t jenkins-pipeline .'
                bat 'cd azure-vote && docker images -a'
            }
        }
        stage('Start test app') {
         steps {
               bat 'docker-compose up -d'
               bat 'cd scripts && test_container.ps1'
         }
         post {
            success {
               echo "App started successfully :)"
            }
            failure {
               echo "App failed to start :("
            }
         }
        }
        stage('Run Tests') {
            steps {
                bat 'pytest ./tests/test_sample.py'
            }
        }
        stage('Stop test app') {
            steps {
                bat 'docker-compose down'
            }
        }
    }   
}
