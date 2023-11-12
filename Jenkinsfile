pipeline {
    agent any

    stages {
        stage('Récupérer le dépôt') {
            steps {
                git credentialsId: 'GitHubSSH', url: 'git@github.com:MoradDev/HelloJava.git'

            }
        }

        stage('Compilation et exécution') {
            steps {
                sh 'javac Hello.java'

                sh 'java Hello'
            }
        }

        stage('Créer et pousser un tag') {
            steps {
                script {
                    def gitTag = "v${BUILD_NUMBER}"
                    sh "git tag ${gitTag}"
                    sh "git push origin ${gitTag}"
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline terminé avec succès.'
        }
        failure {
            echo 'Pipeline échoué.'
        }
    }
}
