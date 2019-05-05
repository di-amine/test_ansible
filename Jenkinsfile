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
               git branch: 'features/mohamed_didi', url: 'https://github.com/DevOps2019s1/tp-ansible.git'
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
        stage('Ansible playbook') {
            steps {
                ansiblePlaybook(credentialsId: 'private_key', inventory: 'hosts.ini', playbook: 'InstalApache.yml') 
            }
        }
    }
}
