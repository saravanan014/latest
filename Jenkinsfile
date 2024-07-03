pipeline {
    agent any
 
    environment {
        // Define the path to your Helm chart directory relative to the cloned repository
        HELM_CHART_DIR = '/home/test3/TEATOM_SCRIPTSTORE'
    }
 
    stages {
        stage('Clone Repository') {
            steps {
                // Clone the repository containing the Helm chart
                git 'https://github.com/saravanan014/latest.git'
            }
        }
 
        stage('Run Checkov') {
            steps {
                // Run Checkov to scan the Helm chart directory
                sh "checkov -d ${HELM_CHART_DIR}"
            }
        }
    }
 
    post {
        always {
            // Clean up after the build
            cleanWs()
        }
        success {
            echo 'Checkov scan completed successfully!'
        }
        failure {
            echo 'Checkov scan failed!'
        }
    }
}
