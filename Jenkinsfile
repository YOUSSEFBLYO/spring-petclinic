pipeline {
    agent any

    parameters {
        string(
            name: 'VERSION',
            defaultValue: '1.0.0',
            description: 'Version à déployer'
        )

        choice(
            name: 'ENVIRONMENT',
            choices: ['TEST', 'PREPROD', 'PROD'],
            description: 'Environnement cible'
        )
    }

    stages {
        stage('Informations et compilation') {
            steps {
                echo '=================================='
                echo 'Application : Spring PetClinic'
                echo "Version     : ${params.VERSION}"
                echo "Environnement : ${params.ENVIRONMENT}"

                sh './mvnw clean package -DskipTests'
            }
        }

        stage('Tests') {
            steps {
                sh './mvnw test'
            }
        }

        stage('Deploy Simulation') {
            steps {
                echo 'Déploiement simulé de Spring PetClinic'
                echo "Version : ${params.VERSION}"
                echo "Environnement : ${params.ENVIRONMENT}"
                echo 'DEPLOYMENT_SUCCESS'
            }
        }
    }

    post {
        success {
            echo 'PIPELINE_SUCCESS'
        }

        failure {
            echo 'PIPELINE_FAILED'
        }
    }
}