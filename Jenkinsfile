pipeline {
    agent any

    environment {
        SONAR_SCANNER_HOME = '/opt/sonar-scanner-5.0.1.3006-linux'
    }

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
                 
                        sh "${env.SONAR_SCANNER_HOME}/bin/sonar-scanner " +
                            "-Dsonar.projectKey=spring-boot-demo " +
                            "-Dsonar.sources=src " +
                            "-Dsonar.host.url=http://34.87.35.49:9000/ " +
                            "-Dsonar.login=75dc7b0013de66f73b58bfb72da63f5ec571bd"
                 
                }
            }
        }
    }

    // Post-build actions and other configurations go here
}
