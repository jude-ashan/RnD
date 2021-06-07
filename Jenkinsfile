pipeline {
    agent any
    def app

    stages {
        stage('Verify Branch') {
            steps {
                echo "$GIT_BRANCH"
            }
        }
        stage('Build image') {
            steps {
                sh(script: """
                  cd Docker/
                  docker images -a
                  app = docker.build(jenkinspipelinestest/0008)
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
        stage ('Push Docker image to Artifact') {
            docker.withRegistry('https://registry.hub.docker.com', 'DockerHub') {
                app.push('0008/jenkinspipelinestest:latest')
            }
        }
    }
}
