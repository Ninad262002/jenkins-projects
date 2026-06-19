pipeline {
agent any

triggers {
     githubPush()   
}
environment {
   APP_SERVER = "172.31.26.200"
}
stages {
stage('checkout') {
steps {
git branch: 'main', url: 'https://github.com/Ninad262002/jenkins-projects.git'
}
}
stage('deploy website') {
steps {
sshagent(credentials: ['ec2-ssh-key']) {
sh """
scp -o StrictHostKeyChecking=no index.html ubuntu@${APP_SERVER}:/tmp/
ssh -o StrictHostKeyChecking=no ubuntu@${APP_SERVER} 'sudo cp /tmp/index.html /var/www/html/index.html'
"""
}
}
}
}
}