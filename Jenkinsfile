pipeline {
    agent any

    stages {
        stage('Checkout Main') {
            steps {
                checkout scm
            }
        }

        stage('Run Script') {
            steps {
                sh 'chmod +x s.sh'
                sh './s.sh'
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

