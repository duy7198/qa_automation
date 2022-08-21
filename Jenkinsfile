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
                bat 'cd C:\Users\DELL\Documents\jenkins\azure-vote\'
                bat 'docker images -a'
                bat 'docker build -t jenkins-pipeline .'
                bat 'docker images -a'
                bat 'cd ..'
            }
        }
    }   
}
