pipeline {
    agent vagrant
    stages {
      stage('checkout') {
            steps {
               git branch: 'features/mohamed_didi', url: 'https://github.com/DevOps2019s1/tp-ansible.git'
            }
        }       
        stage('Ansible Init') {
            steps {
                // script {
                //     def tfHome = tool name: 'Ansible'
                //     env.PATH = "${/usr/bin/ansible}:${env.PATH}"
                //     sh 'ansible --version'
                // }
                tool name: 'Ansible', type: 'ansible'
                sh 'ansible --version'
            }
        }
    }
}
