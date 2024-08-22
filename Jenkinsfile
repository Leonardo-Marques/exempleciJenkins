pipeline {
    agent any

    stages {
        stage('Clonar Repositório') {
            steps {
                git branch: 'main', url: 'https://github.com/Leonardo-Marques/exempleci'
            }
        }

        stage('Instalar Dependências') {
            steps {
                script {
                    sh 'npm install'
                }
            }
        }

        stage('Rodar Testes') {
            steps {
                script {
                    sh 'npm run test:log'
                }
            }

            post {
                always {
                    archiveArtifacts artifacts: 'test-results.log', allowEmptyArchive: true
                }
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'test-results.log', allowEmptyArchive: true
        }
    }
}