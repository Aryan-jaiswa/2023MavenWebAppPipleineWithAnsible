pipeline {
    agent any

    options {
        skipDefaultCheckout(true)
    }

    tools {
        maven 'Maven3'
    }

    stages {

        stage('Checkout') {
            steps {
                deleteDir()   // 🔥 THIS FIXES EVERYTHING
                git branch: 'master', url: ''
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Debug') {
            steps {
                sh 'pwd'
                sh 'ls -l target'
                sh 'cat playbook.yml'   // 🔥 SEE WHICH PLAYBOOK IS USED
            }
        }

        stage('Deploy') {
            steps {
                sh 'ansible-playbook playbook.yml -i hosts.ini'
            }
        }
    }
}
