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
                pwsh(script: """
                cd azure-vote/
                docker images -a
                docker build -t jenkins-pipeline .
                docker images -a
                cd ..
            """)
            }
        }
    }   
}
