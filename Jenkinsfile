pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/PrasanthKumar0/-jenkins-ansible-playbook-tomcat9-setup.git'
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                ansiblePlaybook credentialsId: 'Jenkins-Ansible', disableHostKeyChecking: true, installation: 'Ansible', inventory: '/home/ubuntu/inventory.ini', playbook: 'install_tomcat9.yml', vaultTmpPath: ''
            }
        }
    }

    post {
        success {
            echo 'Tomcat9 installation completed successfully.'
        }

        failure {
            echo 'Tomcat9 installation failed.'
        }
    }
}
