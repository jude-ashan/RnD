pipeline {
    agent any

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
        }
    }
}
