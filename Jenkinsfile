pipeline {

    agent any

    tools {
        nodejs 'nodejs'
    }
    stages {

        stage("install") {

            steps {
                sh 'npm install'
            }
        }
        stage("build") {

            steps {
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
            }
        }
                stage("deploy") {

            steps {
                echo 'deploying the application'
            }
        }
    }
}
