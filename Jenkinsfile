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
        
        stage("Build") {
            steps {
                sh "mvn clean package"
            }
        }
        
        stage("Test") {
            steps {
                sh "mvn test"
            }
        }
    }

    // Post-build actions and other configurations go here
}
