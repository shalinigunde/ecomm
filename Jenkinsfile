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
                git 'https://github.com/Raghava1201/ecomm.git'
            }
        }
         stage('Delete default page') {
            step {
                sh 'sudo rm -rf /var/www/html/*'
            }
        }
         stage('copy to web server') {
            step {
                sh 'sudo cp -rf /var/lib/jenkins/workspace/ecomm/* /var/www/html/'
            }
        }
         stage('update nginx') {
            step {
                sh 'sudo systemctl restart nginx'
            }
        }
         stage('sucess') {
            step {
                echo 'deployment success'
            }
        }
         stage('If failure') {
            step {
                echo 'deployment failure'
            }
        }
    }
}   
