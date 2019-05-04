pipeline {
    agent {
      label 'Vagrant'
    }
    stages {
      stage('checkout') {
            steps {
                git branch: 'master', credentialsId: '70ecb8f7-b239-431a-af07-c9049a10d012', url: 'https://github.com/di-amine/test_ansible.git'            
            }   
      }    
      stage('Ansible Init') {
            steps {
                script {
                    def tfHome = tool name: 'Ansible'
                    env.PATH = "${/usr/bin/ansible}:${env.PATH}"
                    sh 'ansible --version'
                }
            }
        }
    }
}
