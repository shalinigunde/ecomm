pipeline {
    agent any
      stages{
        stage('notification'){
            steps{
                echo 'deployment started'
            }
        }
         stage('install nginx'){
            steps{
                sh 'sudo apt install nginx -y'
            }
        }
         stage('checkout'){
            steps{
                git 'https://github.com/Raghava1201/ecomm.git'
            }
        }
         stage('Delete default page'){
            steps{
                sh 'sudo rm -rf /var/www/html/*'
            }
        }
         stage('copy to web server'){
            steps{
                sh 'sudo cp -rf /var/lib/jenkins/workspace/ecomm/* /var/www/html/'
            }
        }
         stage('update nginx'){
            steps{
                sh 'sudo systemctl restart nginx'
            }
        }
         stage('sucess'){
            steps{
                echo 'deployment success'
            }
        }
         stage('If failure'){
            steps{
                echo 'deployment failure'
            }
        }
    }
}   
