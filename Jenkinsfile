pipeline {
    agent any

    options {
        skipDefaultCheckout(true)
        timeout(time: 5, unit: 'MINUTES')
    }

    parameters {
        booleanParam(
            name: 'RUN_APP',
            defaultValue: true,
            description: 'Run application verification'
        )
    }

    stages {

        stage('Checkout') {
            steps {
                deleteDir()
                checkout scm
            }
        }

        stage('Verify') {
            steps {
                bat 'git --version'
                bat 'java -version'
                bat 'mvn -version'

                script {
                    if (params.RUN_APP) {
                        echo 'RUN_APP is enabled'
                    } else {
                        echo 'RUN_APP is disabled'
                    }
                }
            }
        }
    }
}