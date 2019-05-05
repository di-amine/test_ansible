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
               git branch: 'dev', credentialsId: '70ecb8f7-b239-431a-af07-c9049a10d012', url: 'https://github.com/di-amine/test_ansible.git'
            }
        }       
        stage('Ansible tool') {
            steps {
                script {
                    def tfHome = tool name: 'Ansible'
                    env.PATH = "${tfHome}:${env.PATH}"
                    sh 'ansible --version'
                }
            }
        }
        stage('Ansible playbooks') {
            steps {
                ansiblePlaybook(credentialsId: 'private_key', inventory: 'hosts.ini', playbook: 'InstalApache.yml') 
            }
            steps {
                ansiblePlaybook(credentialsId: 'private_key', inventory: 'hosts.ini', playbook: 'copy_mySSHKey.yml') 
            }
        }
    }
}
