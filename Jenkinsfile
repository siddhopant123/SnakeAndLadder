pipeline {
    agent any
    stages {
        stage('Checkout SCM') {
            steps {
                // Checkout the GitHub repository
                git url: 'https://github.com/siddhopant123/SnakeAndLadder.git', branch: 'master'
            }
        }
        stage('Build') {
            steps {
                script {
                    // Use the Maven tool configured in Jenkins
                    def mvnHome = tool name: 'Default Maven', type: 'maven'
                    // Run Maven commands
                    sh "${mvnHome}/bin/mvn clean install"
                }
            }
        }
        stage('SonarQube Analysis') {
            steps {
                script {
                    // Use SonarQube environment configured in Jenkins
                    withSonarQubeEnv('sq1') { // Replace 'sq1' with the name of your SonarQube server
                        def mvnHome = tool name: 'Default Maven', type: 'maven'
                        sh "${mvnHome}/bin/mvn sonar:sonar -Dsonar.projectKey=snake-ladder-project -Dsonar.projectName='Snake Ladder Project'"
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
