pipeline {
    agent any

    stages {
        stage('Verify Branch') {
            steps {
                echo "$GIT_BRANCH"
            }
        }
        stage('Docker Build') {
            steps {
                sh(script: 'docker images -a')
                sh(script: """
                  cd Docker/
                  docker images -a
                  docker build -t jenkins-pipeline
                  docker images -a
                  cd ..
                  """)
            }
            post {
                success {
                    echo "Docker build is successfull :)"
                }
                failure {
                    echo "Docker build is failed :("
                }
            }
        }
    }
}
