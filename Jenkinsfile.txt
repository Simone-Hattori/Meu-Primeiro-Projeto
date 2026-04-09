pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Simone-Hattori/Meu-Primeiro-Projeto.git'
            }
        }

        stage('Build') {
            steps {
                sh './build.sh'
            }
        }

        stage('Testes') {
            steps {
                sh './test.sh'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executado com sucesso 🎉'
        }
        failure {
            echo 'Pipeline falhou ❌'
        }
    }
}