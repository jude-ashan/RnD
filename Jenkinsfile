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
//        stage('Hello World Build') {
//            steps {
//                  sh(script: """
//                  java -cp helloworld-1.0.jar com.coveros.demo.helloworld.HelloWorld
//                  """)
//            }
//            post {
//                success {
//                    echo "Java build is successfull :)"
//                }
//                failure {
//                    echo "Java build is failed :("
//                }
//            }
//        }

//        stage('Docker Tag') {
//            steps {
//                sh (script: 'docker image tag jenkins-pipeline:latest 0008/jenkins-pipeline:1')
//            }
//        }
//        stage('Push Container') {
//            steps {
//                echo "Workspace is $WORKSPACE"
//                dir("$WORKSPACE/Docker") {
//                    script {
//                        docker.withRegistry('https://registry.hub.docker.com', 'DockerHub') {
//                            def image = docker.build('0008/jenkinspipelinestest:latest')
//                            image.push()
//                        }
//                    }
//                }
//            }
//        }
    }
}
