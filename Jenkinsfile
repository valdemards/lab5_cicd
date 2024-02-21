pipeline {

    agent any

    stages {

        stage("install") {

            steps {
                echo 'installing the application'
            }
        }
        stage("build") {

            steps {
                echo 'building the application'
            }
        }
        stage("test") {

            steps {
                echo 'testing the application'
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
    post {
        
    }
}
