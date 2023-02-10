pipeline {
    agent any
    stages {
        stage('git clone'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'GITLAB_ID_SRK', url: 'http://ec2-65-1-204-222.ap-south-1.compute.amazonaws.com/cloud4c/cloud4c-poc/jenkins-cicd-php-demo.git']]])
            }
        }
    stage('Copy files to Target Host'){
        steps{
    sshagent(['jenkins-ec2-user-raj']) {
       sh 'ssh -o StrictHostKeyChecking=no ubuntu@ip-172-31-5-131'
       sh 'scp -rp /var/lib/jenkins/workspace/demo-php-github/* ubuntu@ip-172-31-5-131:/var/www/html/'
    }
         }
    }
}
}

