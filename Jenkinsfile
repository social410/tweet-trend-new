pipeline {
    agent {
        node {
            label 'maven'
        }
    }

    stages {
        stage('Clone-code') {
            steps {
                git branch: 'main', url: 'https://github.com/social410/tweet-trend-new.git'
            }
        }

        stage('SonarQube analysis') {
        environment {
            scannerHome = tool 'welchmaxwell-sonar-scanner'
        }
        steps{
        withSonarQubeEnv('welchmaxwell-sonarqube-server') { // If you have configured more than one global server connection, you can specify its name
        sh "${scannerHome}/bin/sonar-scanner"
    }
    }
}
}
