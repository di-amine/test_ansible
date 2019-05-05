pipeline {
    agent {
        label 'Vagrant'
    }
    parameters { 
        string(name: 'username', defaultValue: 'devops', description: 'username')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'A secret password')
    }
    stages {
      stage('checkout') {
            steps {
               git credentialsId: '853723fd-8875-4d6b-bc7c-76f9604f2bdc', url: 'https://github.com/di-amine/test_ansible.git'
            }
        }       
        stage('Ansible Init') {
            steps {
                script {
                    def tfHome = tool name: 'Ansible'
                    env.PATH = "${tfHome}:${env.PATH}"
                    sh 'ansible --version'
                }
            }
        }
    }
}
