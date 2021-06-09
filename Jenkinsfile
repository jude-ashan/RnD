pipeline {
    agent any
    triggers {
        pollSCM('*/1 * * * *')
    }
    stages {
        stage('Verify Branch') {
            steps {
                echo "$GIT_BRANCH"
            }
        }
        stage('Clean the build') {
            steps {
                sh(script: 'mvn clean package')
            }
            post {
                success {
                    echo "Hello World build is successful :)"
                }
                failure {
                    echo "Hello World build is failed :("
                }
            }
        }
    }
}
