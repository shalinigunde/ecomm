pipeline {
    agent any
    stages {
        stage('notification') {
            step {
                echo 'deployment started'
            }
        }
         stage('install nginx') {
            step {
                sh 'sudo apt install nginx -y'
            }
        }
         stage('checkout') {
            step {
                git ''
            }
        }
    }
}   
