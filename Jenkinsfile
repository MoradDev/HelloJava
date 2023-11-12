pipeline {
    agent any

    stages {
        stage('Récupérer le dépôt') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[url: 'https://MoradDev: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@github.com/MoradDev/HelloJava.git']]])
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
