pipeline {
    agent any

    stages {
        stage('Greeting') {
            steps {
                sh(script: 'echo Hello World')
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
        }
    }
}
