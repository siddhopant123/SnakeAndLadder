pipeline {
    agent any
    stages {
        stage('SCM') {
            steps {
                checkout scm  // Checkout the code from the repository
            }
        }
        stage('Build') {
            steps {
                // Add a build step to compile the code
                sh 'mvn clean install'  // If you're using Maven, this builds the project
                // For Gradle, use: sh './gradlew build'
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
