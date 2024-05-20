pipeline{
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
        stage('delete default page'){
            steps{
                sh 'sudo rm -rf /var/www/html/*'
            }
        } 
         stage('ecomm'){
            steps{
                sh 'sudo cp -rf /var/lib/jenkins/workspace/ecomm-job/* /var/www/html/'
            }
        } 
         stage('restart nginx'){
            steps{
                sh 'sudo systemctl restart nginx'
            }
        }
          stage('If deployment is success'){
            steps{
                echo 'successfully deployed'
            }
        }
         stage('If deployment fails'){
            steps{
                echo 'deployment failure'
            }
        }


    }
}
