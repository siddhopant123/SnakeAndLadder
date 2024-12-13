pipeline {
    agent any
    stages {
        stage('SCM') {
            steps {
                // Checkout the source code from the repository
                checkout scm
            }
        }
        stage('SonarQube Analysis') {
            steps {
                // Use the SonarScanner tool configured in Jenkins
                script {
                    def scannerHome = tool 'SonarScanner'  // Adjust if needed based on your tool configuration in Jenkins
                    withSonarQubeEnv('SonarQube') {       // Replace 'SonarQube' with your SonarQube server name in Jenkins
                        sh "${scannerHome}/bin/sonar-scanner"  // Run the SonarScanner
                    }
                }
            }
        }
    }
    post {
        always {
            // Cleanup or notifications (if necessary)
        }
    }
}
