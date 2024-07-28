pipeline {
    agent any

    environment {
        ANSIBLE_HOST_KEY_CHECKING = 'False'
    }

    stages {
        stage('Clone repository') {
            steps {
                git branch: 'master', url: 'https://github.com/Prakhar8003/CRUD_Pro.git'
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'ssh-key-id', keyFileVariable: 'SSH_KEY')]) {
                    sh 'ansible-playbook -i inventory.ini flaskcrud.yaml'
                }
            }
        }
    }
}
