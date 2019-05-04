pipeline {
    agent {
      label 'Vagrant'
    }
    stages {
      stage('checkout') {
            steps {
               git branch: 'features/mohamed_didi', url: 'https://github.com/DevOps2019s1/tp-ansible.git'
            }
        }       
      stage('Ansible Init') {
            steps {
               sh 'ansible --version'
            }
        }
    }
}
