node {
  stage('SCM') {
    checkout scm: [
      $class: 'GitSCM', 
      branches: [[name: '*/master']], // Or use your desired branch (e.g., '*/main')
      userRemoteConfigs: [[url: 'https://github.com/siddhopant123/SnakeAndLadder.git', credentialsId: 'github-credentials']]
    ]
  }
  
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarScanner';
    withSonarQubeEnv('sq1') {  // Reference your SonarQube server 'sq1' here
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
}
