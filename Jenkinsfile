pipeline {
    agent any
    parameters {
        choice(
            name: 'environment',
            choices: ['test', 'prod', 'stage'],
            description: 'Passing the Environment'
        )
    }
    environment {
        // Here I'm taking the environment variable from params
        ENVIRONMENT = "${environment}"
    }

    stages {
        stage('build') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */
            // acá construyo la imagen con los argumentos respectivos para el ambiente a desplegar
            steps {
                //buildName "#${BUILD_NUMBER}-${ENVIRONMENT}"
                script {
                    sh 'echo im building'
                }
            }
            post {
                //notificación del si fue exitoso o no la etapa
                always {
                    sh 'echo Pasó BUILD IMAGE'
                //slackSend color: "good", message: "Message from Jenkins Pipeline"
                }
                failure {
                    error 'This pipeline stops here!'
                }
            }
        }

        stage('unit test') {
            steps {
                script {
                    sh 'echo im testing'
                }

            }
            post {
                //notificación del si fue exitoso o no la etapa
                always {
                    sh 'echo Pasó stop container'
                }
                failure {
                    error 'This pipeline stops here!'
                }
            }
        }
    }
}
