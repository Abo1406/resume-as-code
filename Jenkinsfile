pipeline {
    agent any

    stages {
        stage('Create the Droplet') {
            steps {
                echo 'Creating the Droplet...'
                sh 'ansible-playbook /root/resume-as-code/Ansible/digitalocean_droplet_setup.yml'
            }
        }
        stage('Install HTTP on the Droplet') {
            steps {
                echo 'Installing HTTP server...'
                sh 'ansible-playbook -i /root/resume-as-code/Ansible/inven.ini /root/resume-as-code/Ansible/installs.yml'
            }
        }
        stage('Create CV file on HTTP main path') {
            steps {
                echo 'Creating CV file...'
                sh 'ansible-playbook -i /root/resume-as-code/Ansible/inven.ini /root/resume-as-code/Ansible/cv.yml'
            }
        }
        stage('Restart HTTPD') {
            steps {
                echo 'Restarting HTTPD service...'
                sh 'ansible-playbook -i /root/resume-as-code/Ansible/inven.ini /root/resume-as-code/Ansible/restart.yml'
            }
        }
    }
}

