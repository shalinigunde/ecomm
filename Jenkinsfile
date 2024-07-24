pipeline {
    agent any
      stages{
        stage ('notification'){
            steps{
                echo 'deployment started'
            }
        }  
      }
     stage('Approval') {
            steps {
                emailext subject: "Deployment Approval for lms service",
                    body: "<a href='${JENKINS_URL}/job/${JOB_NAME}/${BUILD_NUMBER}/input'>click to approve</a>",
                    to: 'shalinibisa10@gmail.com',
                    mimeType: 'text/html',
                    attachLog: true
                script {
                    def Delay = input id: 'Deploy',
                        message: sh(script: '''echo "You are DEPLOYING -->$deployBranch<-- IN PRODUCTION"''', returnStdout: true).trim(),
                        submitter: 'userID1, userID2',
                        parameters: [
                            [$class: 'ChoiceParameterDefinition',
                                choices: ['no', 'yes'].join('\n'),
                                name: 'input',
                                description: 'Please Select "YES" to Build or "NO" to Abort']
                        ]
                    echo "The answer is: ${Delay}"
                    if ("${Delay}" == "yes") {
                        sh '''echo "Deploying in prod"'''
                    } else {
                        sh """
                        echo "exiting not production ready branch"
                        exit 1
                        """
                    }
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
   
