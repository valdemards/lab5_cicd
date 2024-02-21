pipeline {

    agent any

    tools {
        // docker 'docker'
        nodejs 'nodejs'
    }

    stages {
        stage("build") {
            steps {
                echo 'start building the application'
                sh 'npm install'
                echo 'finished building the application'
            }
        }

        stage("test") {
            steps {
                echo 'start testing the application'
                sh 'npm test'
                echo 'finished testing the application'
            }
        }

        stage("docker build") {
            steps {
                echo 'creating docker container'
                script{
                    echo '${BUILD_NUMBER}'
                    echo "${BUILD_NUMBER}"
                    def image = docker.build "multibranch_app:${BUILD_NUMBER}"
                    // sh 'docker build -t multibranch_app:${BUILD_NUMBER} .'
                }
            }
        }
                stage("deploy") {
            steps {
                echo 'deploying the application'
            }
        }
    }
}
