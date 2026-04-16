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
        deleteDir()
        git branch: 'main', url: 'https://github.com/Aryan-jaiswa/2023MavenWebAppPipleineWithAnsible.git'
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
