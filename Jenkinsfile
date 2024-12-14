pipeline {
    agent any
    tools {
        // Reference the installed Gradle tool
        gradle 'Default Gradle' // Replace 'Default Gradle' with your Gradle tool name if different
    }
    stages {
        stage('Checkout SCM') {
            steps {
                git branch: 'master', 
                    url: 'https://github.com/siddhopant123/SnakeAndLadder.git', 
                    credentialsId: 'github-credentials' // Replace with your Jenkins credentials ID
            }
        }
        stage('SonarQube Analysis') {
            steps {
                script {
                    withSonarQubeEnv('sq1') { // Replace 'sq1' with the correct SonarQube server name
                        sh "./gradlew sonar"
                    }
                }
            }
        }
    }
    post {
        always {
            echo 'Pipeline execution completed.'
        }
    }
}
