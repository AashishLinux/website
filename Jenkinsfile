pipeline {
        agent any
        stages {
                stage ('Cloning Site Data') {
                        steps {
                                echo "clone the repo"
                                sh 'rm -rf website'
                                sh 'git clone https://github.com/aashish20010/website.git'
                                }
                }

                stage ('Pushing Data For Deployment') {
                        steps {
                                echo "Pushing Data For Deployment"
                                sh 'ssh root@172.105.47.83     sudo  git -C "/var/www/html/website" pull origin master'
                                }
                }

                stage ('Checking If Host Is Alive') {
                        steps {
                                echo "Checking If Host Is Alive"
                                sh 'ssh root@194.195.119.17    sudo  ping -c2 172.105.47.83'
                                echo "Ping Done And Host Is Reachable"
                                }
                }
                stage ('Curling Site Data ') {
                        steps {
                                echo "Curling Site Data"
                                sh 'curl https://cicd.geekyaashish.tk'
                                echo "Curling Done"
                                }
                }

                stage ('Removing Residue') {
                        steps {
                                echo "Removing Residue"
                                sh   'ssh root@172.105.47.83      sudo  rm -rf /var/www/html/website/Jenkinsfile'
                                echo "You are good to GO!!!!"
                                }
                }
        }
}
