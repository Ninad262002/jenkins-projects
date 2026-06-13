pipeline {
agent any
environment {
   APP_SERVER = "172.31.23.66"
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
scp -o StrictHostKeyChecking=no index.html ec2-user@${APP_SERVER}:/tmp/
ssh -o StrictHostKeyChecking=no ec2-user@${APP_SERVER} 'sudo cp /tmp/index.html /var/www/html/index.html'
"""
}
}
}
}
}