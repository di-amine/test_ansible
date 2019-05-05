pipeline {
    agent {
        label 'Vagrant'
    }
    parameters { 
        string(name: 'username', defaultValue: 'devops', description: 'username')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'A secret password')
        choice( choices: ['Install Apache', 'Install MariaDb'], discription: '', name: 'install_choice:')
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
        stage('Ansible playbook1') {
            when {
                expression { params.install_choice == 'Install Apache' }
            }
            steps {
                ansiblePlaybook(credentialsId: 'private_key', inventory: 'hosts.ini', playbook: 'InstalApache.yml') 
            }
        }
        stage('Ansible playbook2') {
            when {
                expression { params.install_choice == 'Install MariaDb' }
            }
            steps {
                ansiblePlaybook(credentialsId: 'private_key', inventory: 'hosts.ini', playbook: 'mariadb.yml') 
            }
        }
    }
}
