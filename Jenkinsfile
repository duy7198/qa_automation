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
    }   
}
