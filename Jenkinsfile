node {
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
                dir('Docker/') {
                    // some block
                }
            }
            app = docker.build("jenkinspipelinestest/0008")

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
