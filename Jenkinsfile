pipeline {
    agent any
      stages{
        stage ('notification'){
            steps{
                echo 'deployment started'
            }
        }  
      }
      post {
        always {
            emailext (
                to: 'shalinibisa10@gmail.com, raghavarao750@gmail.com, shalinigunde@outlook.com',
                subject: "Job '${env.JOB-4}' (${env.BUILD_NUMBER}) is complete",
                body: "Please check the Jenkins build job at ${env.BUILD_URL}"
            )
        }
    }
}
         stage ('install nginx'){
            steps{
                sh 'sudo apt install nginx -y'
            }
        }
         stage ('Delete default page'){
            steps{
                sh 'sudo rm -rf /var/www/html/*'
            }
        }
         stage ('copy to web server'){
            steps{
                sh 'sudo cp -rf /var/lib/jenkins/workspace/ecomm-job/* /var/www/html/'
            }
        }
         stage ('update nginx'){
            steps{
                sh 'sudo systemctl restart nginx'
            }
        }
         stage ('sucess'){
            steps{
                echo 'deployment success'
            }
        }
         stage ('If failure'){
            steps{
                echo 'deployment failure'
            }
        }
    }   
