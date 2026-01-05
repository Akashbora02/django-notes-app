@Library("Shared") _
pipeline {
    agent {
        label 'webserver'
    }
    stages {
        stage('Clean'){
            steps{
                script{
                clean_ws()
                }
            }
        }
        stage('Checkout') {
            steps {
                script{
                    clone("https://github.com/Akashbora02/django-notes-app.git","main")
                }
            }
        }
        stage('Build') {
            steps {
                script{
                    docker_build("notes-app","latest","akashbora02")
                }
            }
        }
        stage('Push to DockerHub') {
            steps {
                script{
                    docker_push("notes-app","latest","akashbora02")
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the Code'
                sh 'docker compose down && docker compose up -d'
            }
        }
    }
}
