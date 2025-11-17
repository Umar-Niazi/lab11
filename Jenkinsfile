pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }

    stage('Test') {
        when {
            expression { env.BRANCH_NAME == 'main' }
        }
        steps {
            echo 'Testing.. (only on main branch)'
        }
    }


        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished (success or failure).'
        }
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
