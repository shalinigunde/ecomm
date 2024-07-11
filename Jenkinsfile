pipeline {
    agent any
      stages{
        stage ('notification'){
            steps{
                echo 'deployment started'
            }
        }
         stage ('slack-notification'){
            steps{
                slackSend channel: 'devops',
                    color: '439FE0',
                    message: "started ${JOB_NAME} ${BUILD_NUMBER} (<${BUILD_URL}|Open>)",
                    teamDomain: 'raghava-world',
                    tokenCredentialId: 'slack',
                    username: 'jenkins'
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
                sh 'sudo cp -rf /var/lib/jenkins/workspace/ecomm/* /var/www/html/'
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
}   
