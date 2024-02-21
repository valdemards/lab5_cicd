pipeline {

    agent any
    
    tools {
        // docker 'docker'
        nodejs 'nodejs'
    }

    stages {
        stage("build") {
            when {
                branch 'main'
            }
            steps {
                echo 'start building the application'
                sh 'npm install'
                echo 'finished building the application'
            }
        }
        
        stage("test") {
            when {
                branch 'dev'
            }
            steps {
                echo 'start testing the application'
                sh 'npm test'
                echo 'finished testing the application'
            }
        }

        stage("docker build") {
            when {
                branch 'main'
            }
            steps {
                script{
                    mainImage = docker.build "nodemain:${BUILD_NUMBER}"
                }
            }
            when {
                branch 'dev'
            }
            steps {
                script{
                    devImage = docker.build "nodedev:${BUILD_NUMBER}"
                }
            }
        }
                stage("deploy") {
            steps {
                when {
                branch 'main'
            }
                script{
                    mainImage.run(['-p 3000:3000'])
                }
            when {
                branch 'dev'
            }
                script{
                    devImage.run(['-p 3001:3000'])
                }
            }
        }
    }
}
