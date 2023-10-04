pipeline {
    agent any

    stages {
        stage("Checkout from GitHub") {
            steps {
                // Checkout code from the GitHub repository
                script {
                    def gitRepoUrl = 'https://github.com/ceo-pachira/register-app.git'
                    checkout([$class: 'GitSCM',
                        branches: [[name: 'main']],
                        userRemoteConfigs: [[url: gitRepoUrl]]
                    ])
                }
            }
        }
        
        // Add more stages for your build and deployment process as needed
        
        stage("Maven Clean Package") {
            steps {
                sh "mvn clean package"
            }
        }
        
        stage("Maven Test Result") {
            steps {
                sh "mvn test"
            }
        }
         stage("SonarQube Analysis") {
            steps {
                script {
                    withSonarQubeEnv(credentialsId: 'sonarqube') {
                        sh "mvn sonar:sonar"
                    }
                }
            }
        }
    }

    // Post-build actions and other configurations go here
}
