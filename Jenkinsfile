pipeline {
    agent any

    tools {
        maven 'Maven3'   // or whatever your Maven tool is called
    }

    parameters {
        booleanParam(
            name: 'executeTests',
            defaultValue: true,
            description: 'Run Test stage?'
        )
    }

    environment {
        APP_VERSION = '1.0.0'
    }

    stages {
        stage('Build') {
            steps {
                bat 'mvn -v'                       // <-- changed here
                echo "Building version ${APP_VERSION}"
            }
        }

        stage('Test') {
            when {
                expression { params.executeTests }
            }
            steps {
                echo "Executing tests for version ${APP_VERSION}"
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying version ${APP_VERSION}"
            }
        }
    }

    post {
        always {
            echo "Pipeline finished for version ${APP_VERSION}"
        }
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
