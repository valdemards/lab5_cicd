pipeline {

    agent any

    tools {
        nodejs 'nodejs'
    }
    stages {
        stage("build") {

            steps {
                sh 'npm install'
                echo 'building the application'
            }
        }
        stage("test") {

            steps {
                sh 'npm test'
            }
        }
        stage("docker build") {

            steps {
                echo 'creating docker container'
                script {
                    docker.build("multibranch_pipeline:latest")
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
