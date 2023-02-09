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
    sshagent(['raja-ec2-user-php-bcci']) {
       sh 'ssh ec2-user@13.233.215.202'
       sh 'scp /var/lib/jenkins/workspace/phpbcci/* ec2-user@172.31.44.87:/home/ec2-user/php/'
             }
         }
    }
}
}

