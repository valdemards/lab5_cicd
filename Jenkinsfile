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
            steps {
                script {
                    if (env.BRANCH_NAME == 'main') {
                        sh "docker build -t nodemain:${BUILD_NUMBER} ."
                    } else if (env.BRANCH_NAME == 'dev') {
                        sh "docker build -t nodedev:${BUILD_NUMBER} ."
                    }
                }
            }
        }
        
        stage("deploy") {
            steps {
                script {
                    if (env.BRANCH_NAME == 'main') {
                        sh "docker stop nodemain_container || true"
                        sh "docker rm nodemain_container || true"
                        sh "docker run --name nodemain_container -d --expose 3000 -p 3000:3000 nodemain:${BUILD_NUMBER}"
                        sh "docker rmi -f nodemain:${BUILD_NUMBER} || true"
                    } else if (env.BRANCH_NAME == 'dev') {
                        sh "docker stop nodedev_container || true"
                        sh "docker rm nodedev_container || true"
                        sh "docker run --name nodedev_container -d --expose 3001 -p 3001:3000 nodedev:${BUILD_NUMBER}"
                        sh "docker rmi -f nodedev:${BUILD_NUMBER} || true"
                    }
                }
            }
        }
    }
}
