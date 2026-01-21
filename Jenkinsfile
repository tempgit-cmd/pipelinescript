pipeline {
    agent any
    stages {
        stage('Build Main') {
            steps {
                echo "Building the main branch..."
            }
        }
    }
    post {
        success {
            echo "Main branch build successful!"
        }
        failure {
            echo "Main branch build failed!"
        }
    }
}

