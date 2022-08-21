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
                bat 'cd azure-vote/'
                bat 'docker images -a'
                bat 'docker build . -f Dockerfile.txt jenkins-pipeline'
                bat 'docker images -a'
                bat 'cd ..'
            }
        }
    }   
}
