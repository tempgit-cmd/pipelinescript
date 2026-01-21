pipeline {
    agent any

    environment {
        GIT_CREDENTIALS_ID = 'your-credentials-id'  // Replace with your Jenkins Git credentials ID
        MAIN_BRANCH = 'main'
    }

    stages {
        stage('Checkout Feature Branch') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: "${env.BRANCH_NAME}"]],
                          userRemoteConfigs: [[url: 'https://your-repo-url.git', credentialsId: "${env.GIT_CREDENTIALS_ID}"]]])
                echo "Checked out feature branch: ${env.BRANCH_NAME}"
            }
        }

        stage('Merge Main into Feature') {
            steps {
                script {
                    sh """
                    git fetch origin ${env.MAIN_BRANCH}
                    git merge origin/${env.MAIN_BRANCH} -m "Merge ${env.MAIN_BRANCH} into ${env.BRANCH_NAME}"
                    """
                    echo "Successfully merged ${env.MAIN_BRANCH} into ${env.BRANCH_NAME}!"
                }
            }
        }
    }

    post {
        success {
            echo "Feature branch pipeline completed successfully!"
        }
        failure {
            echo "Merge failed. Please resolve conflicts manually."
        }
    }
}

