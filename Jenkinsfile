pipeline {
    agent any   // Runs on any available agent/node

    stages {
        stage('Checkout') {
            steps {
                // If your script is in source control
                checkout scm
            }
        }

        stage('Run Shell Script') {
            steps {
                // Ensure script has execute permissions
                sh 'chmod +x ./s.sh'
                // Run the script
                sh './s.sh'
            }
        }
    }

    post {
        success {
            echo '✅ Script executed successfully!'
        }
        failure {
            echo '❌ Script execution failed.'
        }
    }
}

