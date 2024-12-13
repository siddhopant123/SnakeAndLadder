pipeline {
    agent any
    stages {
        stage('SCM') {
            steps {
                checkout scm
            }
        }
        stage('SonarQube Analysis') {
            steps {
                script {
                    def scannerHome = tool 'SonarScanner'  // Use the correct tool name for SonarScanner
                    withSonarQubeEnv('sq1') {  // Reference the SonarQube server name you defined
                        sh "${scannerHome}/bin/sonar-scanner"
                    }
                }
            }
        }
    }
    post {
        always {
            echo 'This will run always after the pipeline execution.'
        }
    }
}
