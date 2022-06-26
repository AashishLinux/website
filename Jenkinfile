pipeline {
        agent any
        stages {
                stage ('Cloning Site Data') {
                        steps {
                                echo "clone the repo"
                                sh 'rm -rf Jenkins'
                                sh 'git clone https://github.com/aashish20010/Jenkins.git'
                                }
                }

                stage ('Pushing Data For Deployment') {
                        steps {
                                echo "Pushing Data For Deployment"
                                sh '  ssh -i "/var/jenkins_home/workspace/Mailgateway.pem" ec2-user@ip-172-31-25-76.ap-southeast-1.compute.internal                                 sudo  git -C "/var/www/html/Jenkins" pull origin master'
                                }
                }

                stage ('Checking If Host Is Alive') {
                        steps {
                                echo "Checking If Host Is Alive"
                                sh ' ssh -i "/var/jenkins_home/workspace/Mailgateway.pem" ec2-user@ip-172-31-25-76.ap-southeast-1.compute.internal                                 sudo  ping -c2 172.31.25.76'
                                echo "Ping Done And Host Is Reachable"
                                }
                }
                stage ('Curling Site Data ') {
                        steps {
                                echo "Curling Site Data"
                                sh 'curl 172.31.25.76'
                                echo "Curling Done"
                                }
                }

                stage ('Removing Residue') {
                        steps {
                                echo "Removing Residue"
                                sh   'ssh -i "/var/jenkins_home/workspace/Mailgateway.pem" ec2-user@ip-172-31-25-76.ap-southeast-1.compute.internal                                 sudo  rm -rf /var/www/html/Jenkins/Jenkinsfile'
                                echo "You are good to GO!!!!"
                                }
                }
        }
}

