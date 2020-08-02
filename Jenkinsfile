  pipeline {
        agent any
        stage('Pull code from github') {
            steps {
                git branch: 'master',
                url: 'https://github.com/kadumuri1994/react-kafka-integration.git'
            }
        }
        stage('Code Quality Check via SonarQube') {
            steps {
                script {
                    def scannerHome = tool 'sonarqube-scanner';
                    withSonarQubeEnv("sonarqube-container") {
                        sh """
                            ${scannerHome}/bin/sonar-scanner \
                            -Dsonar.projectKey=react-kafka-integration \
                        """
                    }
                }
            }
        }
  }