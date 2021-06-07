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
                  docker build -t jenkins-pipeline .
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
        stage('Push Container') {
            steps {
                echo "Workspace is $WORKSPACE"
                dir("$WORKSPACE/Docker") {
                    script {
                        docker.withRegistry('https://registry.hub.docker.com', 'DockerHub') {
                            def image = docker.build('0008/jenkinspipelinestest:latest')
                            image.push()
                        }
                    }
                }
            }
        }
    }
}
