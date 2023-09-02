pipeline {
    agent {
        node {
            label 'maven'
        }
    }
environment {
    PATH = "/opt/apache-maven-3.9.2/bin:$PATH"
}
    stages {
        stage("build"){
            steps {
                 sh 'mvn clean deploy'
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
}
