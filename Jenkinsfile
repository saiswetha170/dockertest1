pipeline {
    agent any

    stages {
        stage ('Prompt for input') {
            steps {
                script {
                    env.string = input message: 'Please choose the your option',
                             parameters: [string(defaultValue: 'Ready to go?',
                                          description: '',
                                          name: '')]
                }
            }
        }
            stage('Cloning our Git') {
                steps {
                    git 'https://github.com/saiswetha170/dockertest1.git'
                }
            }
            stage('Copy the Index FIles to Nginx Html Folder') {
                steps {
                    sh 'sudo cp /var/lib/jenkins/workspace/Demo-job1/*.* /var/www/html/'
                }
            }
            stage('Restart the NGINX Sever') {
                steps {
                    sh 'sudo systemctl restart nginx'
                    sh 'sudo systemctl status nginx'
                }
            }
            stage('Verifying The Deployment') {
                steps {
                    sh 'ls /var/www/html/'
                }
            }
    }
}
