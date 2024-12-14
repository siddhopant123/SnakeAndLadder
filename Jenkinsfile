node {
  stage('SCM') {
    checkout scm
    // You can also explicitly specify your SCM URL like this:
    // checkout scm: [
    //   $class: 'GitSCM',
    //   branches: [[name: '*/master']],  // Update the branch name if needed
    //   userRemoteConfigs: [[url: 'https://github.com/siddhopant123/SnakeAndLadder.git']]
    // ]
  }

  stage('Build') {
    // Run Gradle build
    sh './gradlew build'
  }

  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarScanner'
    withSonarQubeEnv('sq1') {  // 'sq1' is the name of your SonarQube server configuration in Jenkins
      // SonarScanner will automatically use the token and other configurations from Jenkins
      sh './gradlew sonarqube'
    }
  }
}
