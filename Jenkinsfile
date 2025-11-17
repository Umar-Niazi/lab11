pipeline {
    agent any

    tools {
        maven 'Maven3'   
    }

    environment {
        APP_VERSION = '1.0.0'
    }

    stages {
        stage('Build') {
            steps {
                bat 'mvn -v'
                echo "Building version ${APP_VERSION}"
            }
        }

        stage('Test') {
            when {
                expression { env.BRANCH_NAME == 'main' }
            }
            steps {
                echo "Testing version ${APP_VERSION}"
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
