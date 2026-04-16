pipeline {
    agent any

    options {
        skipDefaultCheckout(true)
    }

    environment {
        LANG = 'en_US.UTF-8'
        LC_ALL = 'en_US.UTF-8'
    }

    tools {
        maven 'Maven3'   // make sure this exists in Jenkins
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
                echo 'Pipeline is running...'
                sh 'pwd'
                sh 'ls -l'
                sh 'ls -l target'
                sh 'cat playbook.yml'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.war', fingerprint: true
            }
        }

        stage('Deploy') {
            steps {
                sh 'ansible-playbook playbook.yml -i hosts.ini'
            }
        }
    }

    post {
        success {
            echo 'Build & Deployment SUCCESS ✅'
        }
        failure {
            echo 'Build FAILED ❌'
        }
    }
}
