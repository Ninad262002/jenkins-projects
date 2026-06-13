pipeline{
    agent any
    environment {
        APP_SERVER = "172.31.23.66"   #private ip of webserver
    }
    stages{
        stage('checkout'){
            steps{
                git branch: 'main', url: 'https://github.com/Ninad262002/jenkins-projects.git'
            }
        }
    }

    stages('deploy website'){
        steps{
            sh 'ssh -o StrictHostKeyChecking=no ec2-user@${APP_SERVER} "sudo rm -rf /var/www/html/*"'
            scp\
            index.html\
            ubuntu@${APP_SERVER}:/var/www/html 
            sudo cp /tmp/index.html /var/www/html/index.html
        }
    }
}