pipeline {
    agent any
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }

    stages {
        stage('Clone') {
            steps {
                git url: 'https://github.com/Madhu0903/sparkjava-war-example.git' , branch: 'master'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Sonar-Analysis'){
            environment {
                scannerHome = tool 'sonarqube_scanner_tool'
            }
            steps{
                withSonarQubeEnv('sonarqube_scanner_server'){
                    sh "sonar-scanner -X"
                    sh "${scannerHome}/bin/sonar-scanner"
}
}
}
    }
}
